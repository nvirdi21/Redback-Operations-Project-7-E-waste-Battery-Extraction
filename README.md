# Redback Operations Project 7 — E-waste Battery Extraction

> Temporary main-branch README for the Redback Operations Project 7 e-waste battery extraction repository.  

![Project](https://img.shields.io/badge/Project-E--waste%20Battery%20Extraction-blue)
![Status](https://img.shields.io/badge/Main%20Branch-Temporary%20Landing%20Page-orange)
![Branches](https://img.shields.io/badge/Team%20Branches-3-green)
![License](https://img.shields.io/badge/License-Apache--2.0-lightgrey)

---

## Project Overview

This repository supports the Redback Operations Project 7 capstone project on **robotic e-waste battery extraction**.

The broader project aims to support safer extraction of lithium-ion batteries from discarded mobile phones. Lithium-ion batteries can create safety risks during recycling if they are punctured, crushed, or handled incorrectly. For this reason, the project combines different technical streams, including computer vision, robotic handling, and system simulation.

The final system direction is expected to involve:

- detecting and segmenting batteries from phone images,
- using perception outputs to support robotic localisation,
- testing or simulating extraction workflows,
- preparing documentation, reports, and reusable project artefacts.

---

## Current Repository Status

At the moment, the `main` branch is a temporary landing branch. It currently contains only the base repository files, while the main team work is separated into active development branches.

Current branch structure:

```text
Redback-Operations-Project-7-E-waste-Battery-Extraction
│
├── main
│   └── Temporary landing branch
│
├── computer-vision
│   └── Computer Vision team branch
│
├── system-simulation
│   └── System Simulation team branch
│
└── robotics
    └── Robotics team branch
```

This README is written to make the repository understandable before all branches are merged into `main`.

---

## Branch Structure

### `main`

The `main` branch is currently the central landing branch.

Current purpose:

- provide the public entry point for the project repository;
- explain the temporary branch structure;
- guide reviewers to the active team branches;
- act as the future merge target for final deliverables.

At this stage, `main` should not be treated as the complete project implementation. It should be updated again after the team branches are merged.

---

### `computer-vision`

The `computer-vision` branch contains the most developed project work currently visible in the repository.

Purpose:

- battery detection and instance segmentation;
- model training and evaluation;
- dataset checking and augmentation;
- trained weights and selected ONNX exports;
- visual comparison outputs;
- Blender synthetic data generation scripts;
- YouTube scraping and auto-segmentation experiments;
- computer vision reports and documentation.

Expected main folder:

```text
computer_vision/
```

Main computer vision models include:

| Model | Role |
|---|---|
| YOLOv5n-seg | Lightweight YOLO segmentation baseline |
| YOLOv7-seg / YOLOv7-tiny-seg | YOLO segmentation comparison |
| YOLOv8n-seg | Main deployment-oriented model |
| YOLO11n-seg | Newer YOLO segmentation comparison |
| YOLO26n-seg | Experimental YOLO comparison |
| Mask R-CNN R50-FPN | Two-stage instance segmentation baseline |
| PointRend Mask R-CNN | Boundary-aware segmentation comparison |
| RTMDet-Ins tiny | Lightweight MMDetection-based segmentation experiment |
| RetinaNet | Bounding-box detection baseline |
| SSD | Fast detection baseline |

The computer vision work currently recommends **YOLOv8n-seg** as the strongest deployment-oriented model because it provides a good balance between segmentation quality, inference speed, and centroid localisation.

---

### `system-simulation`

The `system-simulation` branch is intended for the system simulation team.

Expected purpose:

- simulation environment setup;
- digital testing of the extraction workflow;
- possible Isaac Sim, MATLAB, or related simulation integration;
- system-level validation before physical deployment;
- documentation of simulation assumptions, scenes, and test cases.

Current note:

```text
This branch currently appears to contain only base repository files.
More detailed documentation should be added when the simulation team files are available.
```

---

### `robotics`

The `robotics` branch is intended for the robotics team.

Expected purpose:

- robotic extraction workflow;
- robot control or motion planning;
- gripper/end-effector logic;
- possible integration with perception outputs;
- physical or simulated robot execution documentation.

Current note:

```text
This branch currently appears to contain only base repository files.
More detailed documentation should be added when the robotics team files are available.
```

---

## Suggested Final Repository Structure After Merge

After all branches are merged into `main`, the repository could be organised as:

```text
Redback-Operations-Project-7-E-waste-Battery-Extraction/
│
├── computer_vision/
│   ├── README.md
│   ├── codes/
│   ├── scripts/
│   ├── weights/
│   ├── onnx/
│   ├── assets/
│   ├── Documents/
│   └── requirements.txt
│
├── system_simulation/
│   ├── README.md
│   ├── scenes/
│   ├── scripts/
│   ├── configs/
│   ├── results/
│   └── docs/
│
├── robotics/
│   ├── README.md
│   ├── control/
│   ├── planning/
│   ├── integration/
│   ├── configs/
│   └── docs/
│
├── docs/
│   ├── final_report/
│   ├── architecture/
│   └── meeting_or_project_notes/
│
├── LICENSE
└── README.md
```

The exact final folder names should match the files provided by each team.

---

## How to Access Each Branch

### Clone the repository

```bash
git clone https://github.com/tthanh05/Redback-Operations-Project-7-E-waste-Battery-Extraction.git
cd Redback-Operations-Project-7-E-waste-Battery-Extraction
```

### View available branches

```bash
git branch -a
```

### Switch to a team branch

Computer Vision:

```bash
git checkout computer-vision
```

System Simulation:

```bash
git checkout system-simulation
```

Robotics:

```bash
git checkout robotics
```

### Clone one branch directly

Computer Vision:

```bash
git clone -b computer-vision https://github.com/tthanh05/Redback-Operations-Project-7-E-waste-Battery-Extraction.git
```

System Simulation:

```bash
git clone -b system-simulation https://github.com/tthanh05/Redback-Operations-Project-7-E-waste-Battery-Extraction.git
```

Robotics:

```bash
git clone -b robotics https://github.com/tthanh05/Redback-Operations-Project-7-E-waste-Battery-Extraction.git
```

---

## Computer Vision Quickstart

The computer vision branch currently contains the most complete technical workflow.

After switching to the `computer-vision` branch:

```bash
cd computer_vision

# Install dependencies
pip install -r requirements.txt

# Download or prepare dataset
bash download_dataset.sh
# or on Windows:
download_dataset.bat

# Check dataset image-label matching
python scripts/check_dataset.py

# Run YOLOv8n-seg inference on one image
yolo task=segment mode=predict \
  model=weights/yolov8n-seg_best.pt \
  source=path/to/test_image.jpg \
  imgsz=640 \
  conf=0.25
```

Python inference example:

```python
from ultralytics import YOLO

model = YOLO("weights/yolov8n-seg_best.pt")

results = model.predict(
    source="path/to/test_image.jpg",
    imgsz=640,
    conf=0.25,
    save=True
)
```

---

## Dataset Note

The full computer vision dataset may not be stored directly in the repository because of file size and access limitations.

The expected dataset format is a YOLO segmentation layout:

```text
final_dataset/
├── dataset.yaml
├── images/
│   ├── train/
│   ├── val/
│   └── test/
└── labels/
    ├── train/
    ├── val/
    └── test/
```

The target class is:

```text
battery
```

The label format is YOLO polygon segmentation format:

```text
class_id x1 y1 x2 y2 x3 y3 ... xn yn
```

For this project:

```text
class_id = 0
class_name = battery
```

---

## Recommended Merge Plan

Before merging the team branches into `main`, each branch should ideally include:

1. a clear folder-level README;
2. a reproducible setup guide;
3. a description of important files;
4. any required dataset/model access notes;
5. expected input and output formats;
6. screenshots, figures, or result examples;
7. known limitations and future work.

Suggested merge order:

1. Merge `computer-vision` once large files, README, and dataset notes are checked.
2. Merge `system-simulation` after simulation files and usage instructions are added.
3. Merge `robotics` after robotics files and integration instructions are added.
4. Update this root README to describe the final merged repository structure.

---

## Temporary Documentation Notes

This README is intentionally conservative because the branch contents are still being organised.

It should be updated again when:

- all team branches have been merged;
- final folder names are confirmed;
- dataset/model access instructions are finalised;
- simulation and robotics files are added;
- final project demonstration instructions are available;
- final reports and presentation artefacts are linked.

---

## License

This repository is released under the Apache-2.0 License. See:

```text
LICENSE
```

for the full license text.

---

## Acknowledgement

This project was developed as part of the Redback Operations Project 7 e-waste battery extraction capstone project. The current repository is organised around separate team branches for computer vision, system simulation, and robotics, with `main` acting as the temporary landing branch until the final merge is completed.
