# 🚗 Car Accident Detection and Deformation Classification Using YOLOv5

This project uses **YOLOv5** to detect car accidents from images and classify the severity of damage into five categories based on visual deformation. The model is trained on a custom annotated dataset of real-world car accidents.

---

## 📂 Dataset Structure

The dataset contains two main folders: `images/` and `labels/`, each with `train/` and `val/` subfolders:

```
dataset/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
```

Each `.txt` label file follows YOLO format:  
`<class_id> <x_center> <y_center> <width> <height>` (all normalized)

Example:
```
4 0.560967 0.598094 0.829009 0.629283
```

---

## 🏷️ Class Labels

| Class ID | Description             | Estimated Deformity |
|----------|--------------------------|----------------------|
| 0        | No Accident              | 0%                   |
| 1        | Minor Accident           | ~30%                 |
| 2        | Moderate Accident        | ~50%                 |
| 3        | Severe Accident          | ~70%                 |
| 4        | Totaled Vehicle          | ~100% (on fire, flipped, crushed) |

---

## 🛠️ Model Training

- **Base Model**: YOLOv5 (`s`, `m`, `l` as needed)
- **Framework**: PyTorch
- **Training Image Size**: 640x640
- **Batch Size**: 16
- **Best Weights**: `weights/best.pt`

### 🔧 Training Command

```bash
python train.py --img 640 --batch 16 --epochs 100 \
--data dataset.yaml --weights yolov5s.pt --name accident_detector
```

---

## 🔍 Inference Example

```bash
python detect.py --weights weights/best.pt --img 640 --source data/test_image.jpg
```

Output will be saved in the `runs/detect/` folder.

---

## 📈 Results

Sample detections and training performance plots are included in the `results/` directory. Add your visuals here to showcase model performance.

---

## 📦 Dataset Collection

The dataset was collected using frames extracted from publicly available online videos (YouTube, Facebook, etc.). A Python script was used to extract frames, followed by manual annotation of bounding boxes and classification into five deformity levels based on visual inspection.
please download the dataset :
https://www.kaggle.com/datasets/marslanarshad/car-accidents-and-deformation-datasetannotated
after downloading dataset please update the paths in custom.yaml:


## 📚 Requirements

```bash
pip install -r requirements.txt
```

Dependencies include:
- torch
- torchvision
- opencv-python
- numpy
- matplotlib
- PyYAML

---

## 📁 Repo Contents

- `weights/last.pt` – Trained YOLOv5 weights
- `dataset.yaml` – Training config
- `images/`, `labels/` – Dataset directories
- `detect.py`, `train.py` – Inference and training scripts
- `results/` – Inference outputs
- `README.md` – Project documentation

---

## 📜 License

Open for academic and non-commercial use. If you reuse this dataset or model, please give credit to the original source.

---

## 👤 Author

Developed by **Muhammad Arslan Arshad**  
Custom YOLOv5 model for accident detection and deformation severity classification.
