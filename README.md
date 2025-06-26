
# 🧠 Comparative Evaluation of Object Detection Models: YOLOv8, DETR, YOLO-NAS, and OWL-ViT2

This project presents a comprehensive comparative evaluation of modern object detection models, with an emphasis on both closed-set and open-vocabulary capabilities. We explore and fine-tune several architectures—including CNN-based models (YOLOv8), Transformer-based models (DETR and RF-DETR), NAS-optimized models (YOLO-NAS), and vision-language models (OWL-ViT2)—on the PASCAL VOC 2012 dataset.

## 📌 Project Goals

- Evaluate detection performance across multiple architectures
- Understand model trade-offs in accuracy, inference time, and flexibility
- Explore open-vocabulary detection using vision-language models
- Compare original and production-ready implementations (e.g., DETR vs. RF-DETR)

## 🗃 Dataset

We used the **PASCAL VOC 2012** dataset, downloaded in a pre-split and curated format from [Roboflow](https://universe.roboflow.com/jacob-solawetz/pascal-voc-2012/dataset/13):

- 📦 Total Images: ~17,000  
- 📂 Format: VOC XML, converted to YOLO and COCO as needed  
- 🏷️ Classes: 20 object categories (person, car, dog, bicycle, etc.)

## 🧪 Evaluated Models

| Model       | Type                        | Highlights |
|-------------|-----------------------------|------------|
| **YOLOv8**  | CNN (One-stage detector)    | Fast, efficient, deployable with Ultralytics |
| **YOLO-NAS**| NAS-optimized CNN detector  | Higher mAP, lower latency via architecture search |
| **DETR**    | Transformer-based (set prediction) | End-to-end detection, strong theoretical foundation |
| **RF-DETR** | Production-ready DETR       | Faster convergence, ViT backbone, deformable attention |
| **OWL-ViT2**| Vision-language Transformer | Zero-shot object detection using text prompts |

## 🛠️ Methods

### ✅ Fine-Tuning

- **YOLOv8**: Trained using [Ultralytics](https://github.com/ultralytics/ultralytics) framework with a modified classification head
- **DETR / RF-DETR**: Used PyTorch + Lightning setup. VOC annotations were converted to COCO format. RF-DETR used DINOv2 backbone + deformable attention
- **YOLO-NAS**: Used Roboflow's AutoML tools and Ultralytics export support ([Docs](https://docs.ultralytics.com/models/yolo-nas))
- **OWL-ViT2**: Inference-only using HuggingFace 🤗, enabled zero-shot object detection from prompts

## 📊 Results

### YOLOv8 (Fine-tuned on VOC)

| Model      | mAP@50 | Precision | Recall |
|------------|--------|-----------|--------|
| YOLOv8-N   | 0.70   | 0.71      | 0.60   |
| YOLOv8-M   | 0.71   | 0.73      | 0.61   |
| YOLOv8-L   | 0.74   | 0.77      | 0.64   |
| YOLOv8-X   | 0.76   | 0.79      | 0.67   |

### DETR and RF-DETR (Transformer Models)

| Model           | mAP@50 | Average Recall |
|-----------------|--------|----------------|
| DETR-R50        | 0.720  | 0.710          |
| DETR-R101       | 0.721  | 0.730          |
| RF-DETR (ViT)   | 0.74   | 0.72           |

### OWL-ViT2 (Zero-shot Detection)

| Image | Detected Objects | Confidence |
|-------|------------------|------------|
| 1     | Car, Building     | 0.79, 0.11 |
| 2     | Highway           | 0.15       |
| 3     | Tree              | 0.69       |
| 4     | Building          | 0.14       |
| 5     | Person            | 0.16       |

## 📈 Visual Examples

![YOLOv8 Prediction](assets/yolo_sample.png)
*YOLOv8-X detecting multiple objects in real-world scenes.*

![OWL-ViT2 Result](assets/owlvit_result1.png)
*OWL-ViT2 zero-shot result for classes: `car`, `building`, `person`.*

## 💡 Key Takeaways

- **YOLOv8** provides an excellent balance between speed and accuracy for real-time applications.
- **DETR** offers elegant, end-to-end detection but requires longer training times.
- **RF-DETR** improves on DETR with ViT backbones and deformable attention, making it more usable in production.
- **YOLO-NAS** achieves higher mAP with fewer FLOPs by leveraging neural architecture search.
- **OWL-ViT2** enables zero-shot detection but suffers from lower confidence scores.

## 🧠 Authors

- **Bahar Khatami** — *University of Padova*  
- **Mojtaba Fattah Damavandi** — *University of Padova*

## 📌 Future Work

- Add mAP@0.5:0.95 comparisons across models
- Evaluate on larger datasets (e.g., MS COCO, OpenImages)
- Extend to video-based detection tasks
- Improve OWL-ViT2 by using prompt engineering and better text embeddings
