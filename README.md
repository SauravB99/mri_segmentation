# 🧠 Brain MRI Segmentation using YOLOv8

This project performs **Brain MRI segmentation** on MRI scans using the 
**YOLOv8n-seg (nano segmentation)** architecture. Given an MRI image, the 
model predicts a pixel-level mask highlighting the tumor region if present, 
and classifies the scan as **Positive (tumor)** or **Negative (no tumor)**.

The project was originally built using a **U-Net architecture** built from 
scratch in Keras/TensorFlow and was later migrated to **YOLOv8** for 
improved performance, faster training, and ease of deployment.

---

## 📂 Dataset
- **Name:** LGG MRI Segmentation Dataset
- **Source:** (https://www.kaggle.com/datasets/mateuszbuda/lgg-mri-segmentation)
- **Total files:** 7858 `.tif` files (images + corresponding masks)
- **Classes:** Tumor — Positive (1) / No Tumor — Negative (0)

| Split      | Samples |
|------------|---------|
| Training   | 2946    |
| Validation | 835     |
| Test       | 148     |

> ⚠️ The dataset is **not included** in this repository due to its size.  
> Download it from Kaggle and place it at the path set in `IMAGE_PATH` 
> inside the notebook.

---

## 🏗️ Architecture
- **Model:** YOLOv8n-seg (nano segmentation variant)
- **Pretrained on:** COCO dataset, fine-tuned on LGG MRI data
- **Input size:** 640 × 640
- **Task:** Instance segmentation (pixel-level tumor mask prediction)
- **Parameters:** 3,409,968
- **GFLOPs:** 12.1
- **Training time:** ~0.119 hours (5 epochs on Tesla T4 GPU)

---

## 📊 Results

### Classification Metrics (Test Set)
| Metric    | Score |
|-----------|-------|
| Accuracy  | 0.912 |
| Precision | 0.976 |
| Recall    | 0.769 |
| F1 Score  | 0.860 |

### Segmentation Metrics (Test Set)
| Metric        | Score |
|---------------|-------|
| mAP @ IoU≥0.5 | 0.839 |
| Mean IoU      | 0.777 |

### Training Performance (Final Epoch — Validation Set)
| Metric     | Score |
|------------|-------|
| Box(P)     | 0.885 |
| Recall (R) | 0.794 |
| mAP50      | 0.889 |
| mAP50-95   | 0.642 |
| Mask(P)    | 0.887 |
| Mask R     | 0.794 |
| Mask mAP50 | 0.886 |

---
