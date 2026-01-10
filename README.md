# 🩺 AI-Based Skin Disease Detection using EfficientNetB3

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Keras](https://img.shields.io/badge/Keras-API-red)

## 📌 Project Overview

This project leverages **Deep Learning** and **Transfer Learning** to automate the detection and classification of skin diseases. Utilizing the **EfficientNetB3** architecture—a powerful convolutional neural network known for its efficiency and accuracy—the model is designed to provide high diagnostic precision.

The system classifies skin lesions into **3 distinct categories**:
1. **Benign**
2. **Melanoma** (Malignant)
3. **Non-Melanoma Cancer**

---

## 🧠 Model Architecture & Methodology

### Why EfficientNetB3?
We selected **EfficientNetB3** as the backbone for this project due to its superior performance in image classification benchmarks. It uses compound scaling to uniformly scale network width, depth, and resolution.

### Transfer Learning Strategy
1.  **Pre-trained Backbone:** We utilized **EfficientNetB3** pre-trained on the **ImageNet** dataset to extract robust features. The model is integrated with **Mixed Precision (mixed_float16)** policy for faster training and reduced memory usage.
2.  **Data Augmentation:** To improve generalization, the pipeline includes:
    *   Random Flip (Horizontal & Vertical)
    *   Random Rotation (0.2)
    *   Random Zoom (0.2)
    *   Random Contrast (0.2)
3.  **Custom Head:**
    *   Global Average Pooling 2D
    *   Batch Normalization
    *   Dropout (0.3)
    *   Dense Output Layer (3 classes, Softmax activation, float32)
4.  **Training Phases:**
    *   **Phase 1:** Training top layers only (10 Epochs, LR=1e-3).
    *   **Phase 2:** Fine-tuning the entire model (40 Epochs).

---

## 📂 Dataset Structure

The model expects the dataset to be organized in a standard directory format:

`training/Diseases/` containing:
*   `benign/`
*   `melanoma/`
*   `non_melanoma_cancer/`

*   **Classes:** 3
*   **Input Shape:** `(300, 300, 3)`
*   **Split:** 70% Train, 20% Val, 10% Test

---

## ⚙️ Configuration & Training Parameters

The training pipeline is optimized with the following hyperparameters:

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **Base Model** | EfficientNetB3 | Pre-trained on ImageNet |
| **Input Shape** | 300 x 300 px | Resolution resized for the model |
| **Batch Size** | 8 | Number of images processed per step |
| **Optimizer** | Adam | Learning rate 1e-3 (initial) |
| **Loss Function** | Sparse Categorical Focal Loss | Gamma=2.0, Alpha=0.25 (Handles class imbalance) |
| **Class Weights** | {0: 1.0, 1: 3.0, 2: 1.0} | Higher weight for Melanoma detection |
| **Precision** | Mixed Float16 | Optimized for GPU inference |

---

## 🚀 Installation & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/Suvradip01/Skin-Disease-Detection-CNN.git
cd Skin-Disease-Detection-CNN
```

### 2. Install Dependencies
Ensure you have Python installed, then install the required libraries:
```bash
pip install tensorflow matplotlib numpy
```

### 3. Prepare Data
Place your image dataset folder (e.g., `training/Diseases`) in the root directory.

### 4. Run the Notebook
Launch Jupyter Notebook and open the project file:
```bash
jupyter notebook Test5.ipynb
```
Execute the cells sequentially to load data, build the model, and start training.

---

## 📊 Performance
The model employs **Class Weights** and **Focal Loss** to specifically address the imbalance in medical datasets, ensuring that critical cases like Melanoma are not overlooked. The training process uses **Autotune** for data prefetching to maximize hardware utilization.

---

## 🛠️ Technology Stack
*   **Language:** Python 3
*   **Deep Learning:** TensorFlow, Keras (Functional API)
*   **Data Processing:** NumPy, tf.data API
*   **Visualization:** Matplotlib
