# Human Detection-Based Video Compression for Storage Optimization in Surveillance Videos

### Methodology
The project implements a two-phase methodology for efficient video compression:

1. Frame Filtering Phase:
Frames are filtered to retain only those containing human activity or significant motion. This reduces storage requirements by removing redundant frames while preserving relevant visual data. YOLOv8x detects humans in each frame, storing bounding boxes for detected regions. A sliding window mechanism ensures continuity, retaining frames with recent human presence to avoid missing critical information due to occlusions or model errors.

2. Video Compression Phase:
Retained frames are compressed using the Discrete Wavelet Transform (DWT). Human regions, identified through bounding boxes, are preserved at high quality, while non-human (background) areas are compressed. A binary mask differentiates regions of interest (ROI) from the background. Wavelet decomposition with 'haar' at level 1 reduces background details, achieving efficient compression without significant quality loss. Compressed frames are reassembled and encoded into a video using FFmpeg.

### Results

##### Human Detection Performance (YOLOv8x)
Precision: Averaged at 0.88, demonstrating effective reduction of false positives.
Recall: Averaged at 0.58, indicating some missed detections due to small or distant humans in frames.
F1 Score: Averaged at 0.70, reflecting a good balance between precision and recall.
Average IoU: Achieved 0.46, showing acceptable overlap between predicted and ground truth bounding boxes.

##### Video Compression Performance
PSNR values across all videos exceeded 30 dB, indicating minimal visual degradation between original and compressed frames.
SSIM values averaged above 0.92, confirming strong preservation of structural details.
