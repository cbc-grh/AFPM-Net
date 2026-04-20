# AFPM-Net

AFPM-Net: Spatial-Frequency Fusion and Progressive Feature Learning for Small Object Detection in UAV Aerial Imagery

This repository contains the official implementation of AFPM-Net for UAV small object detection.  
The proposed method is developed based on the [Ultralytics](https://github.com/ultralytics/ultralytics) framework and includes our modifications to the model architecture, training pipeline, evaluation scripts, and visualization tools.

---

## 1. Introduction

Small object detection in UAV aerial imagery is highly challenging due to tiny object size, dense distributions, scale variation, occlusion, low contrast, and background clutter.  
To address these problems, AFPM-Net improves the baseline detector from four aspects:

- **Adaptive Frequency Stem (AFS)** for enhancing shallow edge-aware and frequency-sensitive representations;
- **Progressive Spatial-Conservative Downsampling (PSC)** for reducing structural information loss during downsampling;
- **Multi-scale Feature Fusion Upsampling (MFFU)** for improving multi-scale feature interaction before upsampling;
- **P2-oriented pyramid redesign** for reallocating model capacity from coarse high-level structures to high-resolution prediction features.

AFPM-Net is designed for UAV small object detection and evaluated on **VisDrone2019** and **UAVDT**.


2. Repository Structure

AFPM-Net/
├─ README.md
├─ requirements.txt
├─ environment.yml
├─ AFPM-Net.yaml
├─ datasets/
│  ├─ README.md
│  ├─ UAVDT.yaml
│  └─ VisDrone.yaml
├─ docs/
│  ├─ 1.jpg
│  └─ 2.jpg
├─ tools/
│  ├─ train.py
│  ├─ val.py
│  ├─ predict.py
│  └─ visualize_feature_maps.py
├─ weights/
│  └─ AFPM-Net.pt
└─ ultralytics/


3. Installation
3.1 Create environment
Using conda:

conda env create -f environment.yml
conda activate yolov11

pip install -r requirements.txt

3.2. Environment

Recommended environment:

Python 3.10
PyTorch 2.x
CUDA 11.x / 12.x
Ultralytics-based codebase

4. Dataset Preparation
Please download the datasets from their official sources.

4.1. VisDrone2019
Official website:
https://github.com/VisDrone/VisDrone-Dataset

4.2. UAVDT
Official website:
https://sites.google.com/view/grli-uavdt/

4.3. Dataset configuration
Dataset yaml files are provided in:

text
复制代码
datasets/VisDrone.yaml
datasets/UAVDT.yaml
Please modify the dataset root path in these yaml files according to your local environment.

More details can be found in:

text
复制代码
datasets/README.md

5 Training
Example training command:

bash
复制代码
python tools/train.py
Or modify the configuration in the training script according to your experiment setting.

Main model configuration file:

text
复制代码
AFPM-Net.yaml

6 Validation
Example validation command:

bash
复制代码
python tools/val.py
This script is used to reproduce the quantitative results on VisDrone2019 and UAVDT.

7 Inference
Example prediction command:

bash
复制代码
python tools/predict.py
The prediction results will be saved to the specified output directory.

8. Feature Map Visualization
We provide a visualization script for extracting intermediate feature maps and generating channel-wise average activation maps.

Example:

bash
复制代码
python tools/visualize_feature_maps.py
This script can be used to visualize the outputs of selected layers and generate:

grayscale activation maps,
heatmaps,
overlay visualizations.

9. Pretrained Weights
The pretrained weights can be found in:

text
复制代码
weights/AFPM-Net.pt
If the weight file is not included in the repository, please download it from:

[Download Link Here]

10. Main Results
VisDrone2019
mAP@50: 0.457
mAP@50:95: 0.278
Params: 3.03M
FLOPs: 34.6G
UAVDT
mAP@50: 0.339
mAP@50:95: 0.209

11. Acknowledgement
This project is heavily based on the Ultralytics codebase.
We sincerely thank the Ultralytics team for their excellent open-source work.

Our implementation modifies the original framework for UAV small object detection research, including model architecture design, training configuration, evaluation, and visualization modules.

12. License
This project is released under the AGPL-3.0 License, following the licensing requirements of the upstream Ultralytics codebase.

Please also refer to the original Ultralytics repository for additional licensing details:
https://github.com/ultralytics/ultralytics







