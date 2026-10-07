# Dataset

The original room dataset is intentionally kept outside Git because of its size.

Expected Drive location:

```text
Omokai/digital_twin/room_001/
```

Expected contents:

```text
room_001/
├── images/
├── transforms.json
├── sfm/
├── nerfstudio_data/
│   ├── images/
│   └── transforms.json
├── seed.ply
├── seed_features.ply
└── splat/
```

Capture dataset:
- 152 original images
- 1920×1080

SfM dataset:
- 142 registered images

Do not overwrite the original capture when experimenting with reconstruction.
