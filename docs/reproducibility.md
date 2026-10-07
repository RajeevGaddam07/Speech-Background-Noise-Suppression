# Reproducibility Guide

## Final inference

1. Install MATLAB with Deep Learning Toolbox and Signal Processing Toolbox.
2. Clone or download this repository.
3. Open the repository in MATLAB.
4. Run `src/run_denoising_v7.m`.
5. Select a noisy WAV file when prompted.
6. Inspect the generated WAV, waveform figure, and spectrogram figure.

The script resolves the model path relative to the repository, so it does not depend on the original author's OneDrive directory.

## Important distinction: v7 vs earlier training draft

The final repository intentionally excludes the earlier `ssproject.m` training draft because it was explicitly marked unverified and is not established as the source of the final v7 model.

The two MATLAB files retained for submission are:

- `src/run_denoising_v7.m` — portable final inference script
- `src/test.m` — supplied test/evaluation implementation

The trained v7 model and reported evaluation outputs are retained as the authoritative final artifacts.
