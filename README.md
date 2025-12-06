# 🩺 AI-Based Skin Disease Detection using MobileNetV2

## **A Deep Learning Approach for Automated Dermatological Image Classification**

---

| Status | Model Backbone | Framework | License |
| :---: | :---: | :---: | :---: |
| ✅ **Functional** | MobileNetV2 | TensorFlow / Keras | [![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC) |

---

## 💡 **Introduction**

Skin diseases are a major global health concern, and early diagnosis is crucial. Limited access to dermatologists, especially in remote regions, creates a significant barrier to timely care.

This project addresses this challenge by developing a **deep-learning-based system** for automated classification of skin conditions from images. We utilize **MobileNetV2**, a state-of-the-art, lightweight, and efficient Convolutional Neural Network (CNN) architecture, making the resulting model highly suitable for deployment on mobile devices or low-resource computing systems.

## 🎯 **Research Objectives**

1.  **Develop a reliable machine learning system** for multi-class classification of skin diseases from image data.
2.  Implement **Transfer Learning** using a pre-trained MobileNetV2 model to accelerate convergence and reduce the need for extensive data.
3.  Rigorously **evaluate performance** using training/validation metrics, loss curves, and visual predictions.
4.  Establish a **structured, reproducible workflow** to facilitate future improvements and experimentation.

## 🧠 **Methodology and Architecture**

The system employs a hybrid architecture that balances the efficiency of a pre-trained backbone with a customized classification head.

### 1. Data Preparation

* **Source:** Images are organized into class-specific folders within the `dataset/` directory.
* **Loading:** Utilizes `tf.keras.preprocessing.image_dataset_from_directory()` to handle file loading, shuffling, batching, and label generation.
* **Preprocessing:** All images are resized to a uniform dimension ($190 \times 190$).

### 2. Configuration Parameters

| Parameter | Value |
| :--- | :--- |
| **Image Dimensions** | $190 \times 190 \times 3$ |
| **Batch Size** | 16 |
| **Epochs (Initial Training)** | 50 |
| **Loss Function** | Sparse Categorical Crossentropy |
| **Optimizer** | Adam |
| **Number of Classes** | Determined dynamically from the dataset |

### 3. Model Architecture

| Component | Description | Strategy |
| :--- | :--- | :--- |
| **Base Model** | **MobileNetV2** | Pretrained on ImageNet. Used as a robust feature extractor. Initial layers are **frozen** to preserve learned representations. |
| **Classification Head** | Global Average Pooling, Dense Layer(s), Softmax Layer | Custom layers added on top of the base model to perform domain-specific multi-class classification. |

## 📊 **Results & Interpretation**

The MobileNetV2-based model demonstrates **strong pattern recognition capability** even with limited domain-specific data.

* **Efficiency:** MobileNetV2's architecture ensures the model is fast and compact.
* **Stability:** Transfer learning leads to smooth learning curves and stable accuracy improvement across epochs.
* **Diagnostic Potential:** The approach shows high potential for building efficient diagnostic assistance systems and effective mobile telemedicine tools.

## 📂 **Project Structure**
