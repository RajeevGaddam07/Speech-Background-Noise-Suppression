# Final v7 Results

## Experiment configuration

- Test files: 824
- Training sequences: 12,000
- Validation sequences: 1,500
- Epochs: 30
- BiLSTM hidden units: 256
- Fully connected units: 512
- STFT: 512 / 384 / 512
- Sequence length: 100 frames
- Compression: 0.50
- Training time: 59.44 minutes

## Objective performance

| Metric | Input | Output | Improvement |
|---|---:|---:|---:|
| SNR | 8.450 | 16.630 | +8.180 dB |
| SI-SDR | 8.449 | 16.720 | +8.271 dB |
| SegSNR | 1.519 | 7.827 | +6.308 dB |

## Additional reported values

- Mean predicted mask: 0.5264
- Oracle SI-SDR: 25.970 dB (also reported as 19.706 dB in the supplied summary; the repository preserves the supplied values without altering the source result file)
- Round-trip SNR: Inf dB

## Important reporting note

The supplied `final_results_summary.txt` contains two different Oracle SI-SDR values. This repository does not silently choose between them. The primary headline metrics are taken directly from the unambiguous SNR, SI-SDR, and SegSNR lines.
