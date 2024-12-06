# Human-Detection-Based-Video-Compression

### Methodology
The project implements a two-phase methodology for efficient video compression:

1. Frame Filtering Phase:
Frames are filtered to retain only those containing human activity or significant motion. This reduces storage requirements by removing redundant frames while preserving relevant visual data. YOLOv8x detects humans in each frame, storing bounding boxes for detected regions. A sliding window mechanism ensures continuity, retaining frames with recent human presence to avoid missing critical information due to occlusions or model errors.

2. Video Compression Phase:
Retained frames are compressed using the Discrete Wavelet Transform (DWT). Human regions, identified through bounding boxes, are preserved at high quality, while non-human (background) areas are compressed. A binary mask differentiates regions of interest (ROI) from the background. Wavelet decomposition with 'haar' at level 1 reduces background details, achieving efficient compression without significant quality loss. Compressed frames are reassembled and encoded into a video using FFmpeg.

### Results
Detection Performance: YOLOv8x achieved 0.88 precision, 0.58 recall, and an F1 score of 0.70 on the VIRAT dataset.
Compression Evaluation: An average PSNR of 33.72 dB and SSIM of 0.9237 confirm high visual quality retention with reduced file size.
This approach minimizes storage costs while preserving essential visual details.
