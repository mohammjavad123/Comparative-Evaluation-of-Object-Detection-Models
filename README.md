
# Comparative Evaluation of Object Detection Models

This project presents a comparative study of modern object detection architectures on the PASCAL VOC 2012 dataset. The models evaluated include:

- YOLOv8 (Nano, Small, Medium, Large, X-Large)
- DETR (ResNet-50, ResNet-101)
- RF-DETR
- YOLO-NAS
- OWL-ViT2 (Zero-Shot Detection)

## 🚀 Models & Methodology

### 1. YOLOv8
Trained using the Ultralytics library on VOC-formatted data converted via Roboflow. YOLOv8 variants showed strong real-time performance with increasing accuracy from Nano to X-Large.

### 2. DETR
Fine-tuned Facebook AI's DETR using ResNet backbones. COCO-to-VOC conversion and classification head replacement enabled effective adaptation to the VOC dataset.

### 3. RF-DETR
Based on Roboflow's Deformable DETR with ViT/DINOv2 backbones. Supports real-time inference with over 60 mAP on COCO and seamless Roboflow integration.

### 4. YOLO-NAS
A new hybrid NAS-based model balancing speed and accuracy. Implemented using [DigitalOcean's guide](https://www.digitalocean.com/community/tutorials/yolo-nas#about-the-article) and Roboflow [documentation](https://docs.ultralytics.com/models/yolo-nas/).

### 5. OWL-ViT2
Evaluated without fine-tuning. Zero-shot object detection using natural language prompts and HuggingFace's OWL-ViT2 base model.

## 📊 Results Summary

| Model          | mAP@50 | Precision | Recall |
|----------------|--------|-----------|--------|
| YOLOv8-N       | 0.70   | 0.71      | 0.60   |
| YOLOv8-M       | 0.71   | 0.73      | 0.61   |
| YOLOv8-L       | 0.74   | 0.77      | 0.64   |
| YOLOv8-X       | 0.76   | 0.79      | 0.67   |
| DETR-R50       | 0.720  | —         | 0.710  |
| DETR-R101      | 0.721  | —         | 0.730  |
| RF-DETR        | 0.74   | 0.75      | 0.72   |
| YOLO-NAS       | —      | —         | —      |
| OWL-ViT2       | —      | —         | —      |

_Note: OWL-ViT2 results are qualitative, focusing on zero-shot capability._

## 📄 Report & Full Results

For detailed model architectures, fine-tuning strategies, visualization, and experiment design:
👉 **Please refer to the full report in [`report.pdf`](report.pdf)**

The report includes:
- Detailed methodology and dataset preparation
- Architecture overviews with diagrams
- Evaluation metrics and fine-tuning setup
- All result tables and visualizations

## 🧠 Key Insights

- **YOLOv8-X** outperforms other variants in accuracy but with increased compute.
- **RF-DETR** offers a great tradeoff between accuracy and real-time performance using DINOv2 + deformable attention.
- **DETR** still demonstrates competitive performance with its end-to-end design.
- **OWL-ViT2** enables generalized detection without retraining, valuable for open-set scenarios.

## 📂 Dataset

Dataset used: [Roboflow VOC 2012 Export](https://universe.roboflow.com/jacob-solawetz/pascal-voc-2012/dataset/13)  
Format: VOC (XML), converted as needed

---

Made by Bahar Khatami & Mojtaba Fattah Damavandi  
University of Padova · 2025
