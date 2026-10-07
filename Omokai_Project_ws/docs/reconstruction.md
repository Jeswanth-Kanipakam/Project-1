# Reconstruction Results

## Input

- Device: Google Pixel 9a
- Resolution: 1920 × 1080
- Frames captured: 152

## HLoc/SfM

- SuperPoint: max 4096 keypoints, NMS radius 3, grayscale
- SuperGlue: sequential image matching
- Sequential pairs: 1,465
- Registered images: 142/152
- 3D points: 29,666
- Observations: 214,175
- Mean track length: 7.22
- Mean observations/image: 1,508
- Mean reprojection error: 1.234 px

## Nerfstudio conversion

- Registered images: 142
- Camera model: SIMPLE_RADIAL
- Focal length: 1410.0115 px
- Principal point: (960, 540)
- Output: `nerfstudio_data/transforms.json`

## Current limitation

The Gaussian Splatting training stage has not yet been completed in a clean environment.
