# Methodology

## 1. Problem Definition

Given noisy speech `x[n]`, the objective is to estimate an enhanced speech waveform `y[n]` with reduced background noise and improved objective speech-quality measures.

## 2. Time-Frequency Representation

The final v7 inference pipeline uses a 16 kHz sampling rate and a periodic Hann window with 512 samples, 384 samples of overlap, and a 512-point FFT. The resulting one-sided STFT contains 257 frequency bins.

The noisy magnitude is converted to a logarithmic representation:

`F(k,t) = log(|X(k,t)| + 1e-6)`

The stored v7 feature mean and standard deviation are then applied feature-wise.

## 3. Deep Learning Mask Estimation

The trained network receives the normalized sequence of spectral features and predicts a frequency-dependent speech mask. The documented v7 configuration contains 256 BiLSTM hidden units and a 512-unit fully connected layer, followed by a sigmoid mask output.

The mask is bounded to the interval [0, 1].

## 4. Spectral Enhancement

The predicted mask is multiplied by the noisy magnitude spectrum:

`|Y(k,t)| = M(k,t) * |X(k,t)|`

The noisy phase is retained:

`Y(k,t) = |Y(k,t)| * exp(j angle(X(k,t)))`

## 5. Waveform Reconstruction

The one-sided enhanced spectrum is mirrored to form a full spectrum. Each frame is transformed using the inverse FFT, multiplied by the synthesis window, and overlap-added. Window-power normalization is applied to compensate for overlapping windows.

The reconstructed signal is then trimmed to the original input length, its DC component is removed, and amplitude is limited only when clipping would otherwise occur.

## 6. Evaluation

The supplied v7 results report SNR, SI-SDR, and SegSNR for 824 evaluated files. The reported mean improvements are:

- SNR: +8.180 dB
- SI-SDR: +8.271 dB
- SegSNR: +6.308 dB

The repository also preserves the per-file objective results in `results/objective_results.csv`.
