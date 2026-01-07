# YOLOv8 Crop Disease Detection System

This project implements a **deep learning–based crop disease detection pipeline** using **YOLOv8**, a modern real-time object detection model.  
It detects and classifies multiple crop leaf diseases from images and is suitable for academic projects, agricultural analytics, and applied computer vision use cases.

---

## Project Overview

Crop diseases can significantly reduce agricultural yield and quality. This system uses **computer vision and deep learning** to automatically detect crop diseases from leaf images.

### Key Features
- Multi-class crop disease detection
- YOLOv8-based object detection
- End-to-end pipeline: dataset download → training → validation → inference
- Visualisation of predictions and training metrics
- Runs seamlessly on Google Colab

---

## Model & Approach

- **Model Architecture**: YOLOv8 Nano (`yolov8n`)
- **Task Type**: Object Detection
- **Framework**: Ultralytics YOLOv8
- **Training Strategy**:
  - Pretrained weights for faster convergence
  - Custom dataset in YOLO format
  - Automated loss optimisation and evaluation

---

## Dataset Structure

The dataset follows the standard **YOLO directory format**:
dataset/
├── train/
│ ├── images/
│ └── labels/
├── val/
│ ├── images/
│ └── labels/

2. Install Required Libraries
pip install kaggle ultralytics

3. Configure Kaggle
mkdir -p ~/.kaggle
mv kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json

Dataset Download
The dataset is downloaded directly from Kaggle and extracted locally:
kaggle datasets download -d <dataset-name>
unzip <dataset-name>.zip -d /content/dataset

A YAML configuration file defines dataset paths and class labels:
train: /content/dataset/train/images
val: /content/dataset/val/images
nc: <number_of_classes>
names: [class_1, class_2, ..., class_n]
This file is required by YOLOv8 during training and validation.

Training Parameters
Epochs: 10
Image Size: 640 × 640
Batch Size: 16
Optimizer: Automatically selected by YOLOv8

Evaluation Metrics
Precision
Recall
mAP@0.5
mAP@0.5:0.95
These metrics measure detection accuracy and generalization performance.

Inference & Prediction
results = model.predict(
    source='path/to/images',
    conf=0.5,
    save=True
)

Bounding boxes and class labels are drawn on images
Predictions are saved automatically
Confidence threshold is configurable
Training & Loss Visualization

Metrics Visualized
Precision
Recall
mAP@0.5
Loss Components
Box Loss
Classification Loss
Distribution Focal Loss (DFL)
All plots help analyze convergence and model stability.

Output Directory
All outputs are stored under:
runs/detect/

This includes:
Trained model weights
Validation metrics
Prediction images
Training logs

Applications
Crop disease monitoring
Precision agriculture
Smart farming systems
Agricultural research
AI-based advisory tools

Future Improvements
Support for additional crop species
Real-time camera-based detection
Mobile or web deployment
Disease severity estimation
Integration with weather and soil data

License
This project is intended for educational and research purposes.
Dataset licenses are governed by their respective sources.
