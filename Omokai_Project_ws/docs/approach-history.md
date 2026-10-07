# Reconstruction Approach History

## Phase 1 — Phone capture + Rumahku

Goal: prove that a normal smartphone can capture a room and generate a Gaussian-splat representation.

Result:
- Pixel 9a + ARCore capture worked.
- 152 images were captured.
- ARCore poses and feature points were saved.
- Rumahku generated Gaussian-splat PLY output.

Problem:
- The generated visual reconstruction was not sufficiently usable.
- Debugging the entire phone-side reconstruction stack did not produce a reliable room model.

Decision:
- Keep the capture method.
- Change the reconstruction backend.

## Phase 2 — HLoc / SfM

Goal: obtain a reliable geometric map and camera poses before attempting rendering.

Pipeline:

Images → SuperPoint → SuperGlue → geometric verification → COLMAP/pycolmap SfM

Result:
- 142/152 images registered.
- 29,666 3D points.
- 214,175 observations.
- 1.234 px mean reprojection error.

This is the current validated reconstruction baseline.

## Phase 3 — SfM to Nerfstudio

Goal: use the validated camera poses and images as input to Gaussian Splatting.

Result:
- 142 registered images copied.
- `transforms.json` generated.
- SIMPLE_RADIAL camera model.
- 1920×1080.
- focal length ≈1410 px.
- dataset validation passed.

## Phase 4 — Splatfacto

Goal: train a dense Gaussian-Splat model using the validated SfM geometry.

Status:
- Nerfstudio/gsplat import was tested.
- Initial dependency setup became inconsistent in Colab.
- Training was not completed.

Next action:
- Use a clean compatible environment and train Splatfacto from the validated Nerfstudio dataset.

## Phase 5 — GPS-denied localization

Goal: determine the trainee phone pose relative to the stored room map and compare it with a supervisor-defined target.

Prototype evidence:
- 543 2D→3D correspondences on a held-out frame.
- 398 PnP RANSAC inliers.
- 73.30% inlier ratio.

Next:
- improve relocalization robustness,
- transform pose into canonical room coordinates,
- calculate target distance,
- trigger proximity feedback.
