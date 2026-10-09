# Machine-Learning[report.pdf](https://github.com/delfydavis/Machine-Learning/files/9701741/report.pdf)
<div align="center">

# 🩺 Image Classification of Skin Lesions

### Deep Learning for Multi-Class Skin Lesion Classification

<p>
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white"/>
<img src="https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white"/>
<img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
<img src="https://img.shields.io/badge/AutoKeras-AutoML-6C63FF?style=for-the-badge"/>
</p>

**An image-classification project using the HAM10000 dataset to classify skin lesions into seven categories and distinguish benign from malignant lesions.**

</div>

---

## 🎯 Project Overview

This project explores how deep learning can be applied to **skin lesion image classification**.

Two modelling approaches were investigated:

- **AutoKeras** — automatically searches for a suitable neural-network architecture.
- **InceptionResNetV2** — a pre-trained deep-learning model fine-tuned for the dataset.

The system follows:

```text
HAM10000 Dataset
       ↓
Data Cleaning
       ↓
Exploratory Data Analysis
       ↓
Label Encoding
       ↓
Class Balancing
       ↓
Image Resizing & Normalization
       ↓
Train / Test Split
       ↓
Deep Learning Models
   ┌───┴────────────┐
   ▼                ▼
AutoKeras     InceptionResNetV2
   │                │
   └───────┬────────┘
           ▼
     Model Evaluation
```

---

## 📊 Dataset

The project uses the **HAM10000 (Human Against Machine with 10000 training images)** dataset.

The classification task covers seven lesion categories:

1. Benign keratosis-like lesions
2. Dermatofibroma
3. Melanoma
4. Vascular lesions
5. Basal cell carcinoma
6. Melanocytic nevi
7. Actinic keratoses

The project also performs a binary classification task:

```text
Skin Lesion
    ├── Benign
    └── Malignant
```

The report notes substantial class imbalance in the original data, with **Melanocytic nevi containing 3,527 images**, while Dermatofibroma and Vascular lesions contained only **61** and **71** respectively. fileciteturn0file0L97-L107

---

## 🧹 Data Preparation

The preprocessing pipeline included:

- Removing unused columns
- Removing null values
- Converting `is_benign` from float to integer
- Encoding lesion labels using `LabelEncoder`
- Exploring class distributions
- Balancing classes through resampling
- Creating image paths
- Resizing images to **32 × 32**
- Converting images to NumPy arrays
- Normalizing pixel values from `0–255` to `0–1`
- Splitting the data into **75% training / 25% testing**

The class-balancing step resampled each lesion category to **250 observations** before combining them into the balanced dataset. fileciteturn0file0L109-L125

---

# 🤖 Model Architecture

## 1. AutoKeras

AutoKeras was used as an AutoML approach to search across neural-network configurations and identify a suitable architecture for the dataset.

The reported experiment involved **25 trials**, after which the selected model was trained for:

```text
Batch Size : 16
Epochs     : 50
```

The selected network contained **7 dense layers**. fileciteturn0file0L170-L188

### Tasks

The model was trained for:

```text
Image → Seven Lesion Categories

Image → Benign / Malignant
```

---

## 2. InceptionResNetV2

The second approach used **InceptionResNetV2**, a pre-trained neural network.

The pre-trained architecture was fine-tuned using the project dataset for both:

- Seven-class lesion classification
- Benign vs malignant classification

The report describes the pre-trained model as providing a stronger benchmark than the AutoKeras approach. 

---

# 📈 Results

### Seven-Class Classification

| Model | Reported Accuracy |
|---|---:|
| AutoKeras | **89%** |
| InceptionResNetV2 | **≈88%** |

The AutoKeras model reported approximately **89% accuracy** for the seven-category classification task, while InceptionResNetV2 reported approximately **88%**. 

### Benign vs Malignant

| Model | Reported Accuracy |
|---|---:|
| AutoKeras | **76%** |
| InceptionResNetV2 | **≈77.98%** |

For binary benign/malignant classification, InceptionResNetV2 achieved approximately **77.98%**, compared with **76%** for the AutoKeras model. 

### Overall Comparison

```text
Seven-Class Classification

AutoKeras          ██████████████████  89%
InceptionResNetV2  █████████████████   ≈88%


Benign / Malignant

AutoKeras          ███████████████     76%
InceptionResNetV2  ████████████████    ≈78%
```

The report ultimately preferred **InceptionResNetV2** because of its stronger binary-classification result and comparatively lower validation loss. 

---

# 🔬 Evaluation

The project evaluated model behaviour using:

- Training accuracy
- Validation accuracy
- Training loss
- Validation loss
- Confusion matrix

The AutoKeras experiment includes a confusion matrix for the seven-class classification task, while training/validation curves were used to examine model learning behaviour. 

---

# 🧠 Technical Workflow

```text
                 HAM10000
                    │
                    ▼
              Data Cleaning
                    │
                    ▼
             Class Analysis
                    │
                    ▼
             Label Encoding
                    │
                    ▼
             Class Balancing
                    │
                    ▼
        Image Resize + Normalize
                    │
                    ▼
             Train / Test Split
                    │
             ┌──────┴──────┐
             ▼             ▼
         AutoKeras   InceptionResNetV2
             │             │
             └──────┬──────┘
                    ▼
              Classification
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
     Seven Classes      Benign / Malignant
```

---

# 🛠️ Technology Stack

**Programming**

`Python`

**Deep Learning**

`TensorFlow` `Keras` `AutoKeras` `InceptionResNetV2`

**Data Processing**

`Pandas` `NumPy` `Scikit-learn`

**Computer Vision**

`Image Processing` `Image Normalization` `Data Augmentation / Resampling`

**Development**

`Jupyter Notebook`

---

# 📁 Suggested Repository Structure

```text
skin-lesion-classification/
│
├── README.md
├── notebooks/
│   └── skin_lesion_classification.ipynb
│
├── data/
│   └── README.md
│
├── images/
│   ├── class_distribution.png
│   ├── confusion_matrix.png
│   └── training_curves.png
│
└── report/
    └── project_report.pdf
```

---

# ⚠️ Limitations

The reported results should be interpreted as **experimental machine-learning results**, not as clinical performance.

Key limitations identified in the project include:

- The original dataset was highly imbalanced.
- The balanced modelling dataset used resampling to 250 observations per class.
- Images were resized to only **32 × 32** pixels.
- The reported evaluation uses a relatively limited experimental setup.
- The project notes that expanding the dataset with more of the original images could improve prediction performance.
- Further work could investigate ensemble learning and evolutionary approaches. 

---

# 🚀 Future Improvements

Potential next steps include:

- Train on a larger portion of the original HAM10000 dataset
- Use higher-resolution input images
- Apply stronger augmentation strategies
- Compare additional CNN architectures
- Investigate transfer-learning strategies
- Use class-weighting instead of relying only on resampling
- Perform stronger cross-validation
- Evaluate precision, recall, F1-score and ROC-AUC
- Explore ensemble learning
- Add model interpretability techniques such as Grad-CAM
- Package the model behind an inference API

---

# 🏆 Key Takeaway

This project demonstrates an end-to-end **computer-vision and deep-learning workflow**:

```text
DATA
 ↓
PREPROCESSING
 ↓
EXPLORATION
 ↓
CLASS BALANCING
 ↓
DEEP LEARNING
 ↓
EVALUATION
 ↓
MODEL COMPARISON
```

It combines **data preparation, exploratory analysis, image processing, AutoML, transfer learning and model evaluation** to investigate automated skin-lesion classification.

---

<div align="center">

## 🧠 Computer Vision → Deep Learning → Intelligent Classification

**Exploring how machine learning can transform image-based data into actionable predictions.**

</div>
