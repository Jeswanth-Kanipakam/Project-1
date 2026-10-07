# System Architecture

```text
                    CAPTURE
Physical room ──→ Pixel 9a / ARCore
                         │
                         ▼
                    152 images
                         │
                         ▼
                 Visual reconstruction
                         │
          ┌──────────────┴──────────────┐
          ▼                             ▼
   HLoc / SfM                    Gaussian Splatting
   camera poses                  visual digital twin
   sparse 3D map                       │
          │                             │
          └──────────────┬──────────────┘
                         ▼
                 Canonical room frame
                         │
              Supervisor target point
                         │
                         ▼
                 Trainee enters room
                         │
                         ▼
                Phone visual relocalization
                         │
                         ▼
                 Phone pose in room frame
                         │
                         ▼
                  Distance to target
                         │
                         ▼
                 Beep / proximity alert
```

The key design principle is that reconstruction and localization should remain independently testable.
