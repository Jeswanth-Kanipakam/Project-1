# GPS-Denied Localization

## Goal

Estimate the trainee phone's pose in the canonical room coordinate frame without depending on GPS.

## Prototype

A held-out image was localized against a reconstructed SfM map.

Observed:
- 543 2D→3D correspondences
- 398 PnP RANSAC inliers
- 73.30% inlier ratio
- mean reprojection error ≈1.87 px

## Target workflow

1. Build/reference a room map.
2. Define a target coordinate in the room frame.
3. Capture live camera frames.
4. Extract/match visual features against the reference map.
5. Estimate camera pose with PnP/RANSAC.
6. Convert pose to room coordinates.
7. Compute distance to target.
8. Trigger a proximity/direction signal.

## Important

The MVP does not require object recognition initially. A stored 3D target coordinate is sufficient for the first proximity-alert prototype.
