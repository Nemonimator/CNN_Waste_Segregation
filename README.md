# 🗑️ Waste Material Segregation using CNNs

## 📌 Overview
This project aims to develop an intelligent waste segregation system using Convolutional Neural Networks (CNNs) to automate classification of images into waste categories. Accurate waste classification plays a critical role in enhancing recycling efficiency, minimizing environmental impact, and supporting sustainable management practices.

---

## 🎯 Objectives
- Classify waste materials into seven categories: `Cardboard`, `Food Waste`, `Glass`, `Metal`, `Other`, `Paper`, `Plastic`.
- Handle class imbalance using data augmentation and undersampling strategies.
- Explore transfer learning via MobileNetV2 to boost performance over custom CNNs.
- Generate interpretability metrics like confusion matrices, F1 scores, and specificity/sensitivity.

---

## 📊 Dataset
- Source: Provided as a zipped collection of ~7,625 labeled waste images.
- Structure: Each class stored in a separate folder.
- Resolution: Standardized to `128x128` post-preprocessing.
- Notable imbalance: `Plastic` dominates the dataset, followed by `Food Waste`.

---

## ⚙️ Methodology

### 1. Preprocessing
- Normalized pixel values to `[0, 1]`
- Resized all images to `(128x128)`
- Encoded labels using `LabelEncoder` and `one-hot vectors`
- Split dataset into `75%` training and `25%` validation using stratified sampling

### 2. Augmentation Strategy
- Applied flips, rotations, zooms, and brightness adjustments to underrepresented classes
- Performed class balancing: `undersampled major classes` + `augmented minor ones`
- Final training set size after balancing: **24,705 images**

### 3. Model Architectures
- ✅ **Custom CNN**: 3 convolutional blocks with dropout, batch normalization, and dense layers  
  ↪ Accuracy: ~43%
- ✅ **MobileNetV2 (Transfer Learning)**:  
  - Frozen base layers  
  - GlobalAveragePooling → Dense → Dropout → Softmax  
  ↪ Accuracy: ~72% post-augmentation

### 4. Training
- Used `EarlyStopping` and `ModelCheckpoint` to prevent overfitting
- Applied `class_weight` to counter residual imbalance
- Optimizer: Adam with learning rate `1e-4`
- Loss: Categorical Crossentropy

---

## 🧪 Results & Metrics

| Metric            | Value         |
|-------------------|---------------|
| Final Train Accuracy | 90.06%       |
| Validation Accuracy   | 72.47%       |
| Macro F1 Score        | 0.74          |
| Best Val Loss         | 0.795         |
| Notable Class Gains   | Glass, Other, Paper |

### 🔍 Confusion Matrix & Evaluation
- Precision, Recall, Specificity, and Sensitivity calculated per class
- `Plastic` class showed high precision but lower recall—future work may include focused augmentation

---

## 🔮 Future Work
- Explore Grad-CAM visualizations for interpretability
- Fine-tune upper MobileNetV2 layers for even better recall on ambiguous classes
- Extend to edge deployment using TensorFlow Lite or ONNX

---


---

## 👨‍💻 Author
**Nemello** – Machine learning practitioner with a passion for computer vision, deep CNN architectures, and real-world AI applications.

---

## 📜 License
This project is released under the MIT License.



