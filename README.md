# 🩺 AI-Based Skin Disease Detection using MobileNetV2

## **A Deep Learning Approach for Automated Dermatological Image Classification**

---

| Status | Model Backbone | Framework | License |
| :---: | :---: | :---: | :---: |
| ✅ **Functional** | **MobileNetV2** | **TensorFlow** / **Keras** | [![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC) |

---

## 🚀 **Project Overview**

Skin diseases are a major global health concern, and early diagnosis is crucial. Limited access to dermatologists, especially in remote regions, creates a significant barrier to timely care.

This project addresses this challenge by developing a **deep-learning-based system** for automated classification of multiple skin conditions from images. We leverage **MobileNetV2**—a state-of-the-art, *lightweight and highly efficient* Convolutional Neural Network—making the resulting model ideally suited for deployment on **mobile devices** or in **low-resource computing environments**.

## 🎯 **Research Objectives**

* Develop a **reliable machine learning system** for multi-class classification of skin diseases from image data.
* Implement **Transfer Learning** using a pre-trained **MobileNetV2** model to accelerate convergence and ensure robust feature extraction.
* Rigorously **evaluate performance** using training/validation metrics, loss curves, and visual predictions.
* Establish a **structured, reproducible workflow** to facilitate future improvements and experimentation.

## 🧠 **Methodology and Architecture**

The system utilizes a powerful hybrid architecture that combines the proven efficiency of a pre-trained backbone with a custom classification head tailored for the dermatological domain.

### 1. Dataset Preparation

| Component | Description | Technologies |
| :--- | :--- | :--- |
| **Data Source** | Images organized into class-specific folders (`dataset/`). | Custom |
| **Data Loading** | Handles file loading, shuffling, batching, and label generation dynamically. | `tf.keras.preprocessing.image_dataset_from_directory()` |
| **Preprocessing** | Images are consistently resized and standardized. | Image resizing to **190 × 190** |

### 2. Training Configuration

| Parameter | Value |
| :--- | :--- |
| **Input Image Size** | **$190 \times 190 \times 3$** |
| **Batch Size** | **16** |
| **Epochs (Initial Training)** | **50** |
| **Loss Function** | **Sparse Categorical Crossentropy** |
| **Optimizer** | **Adam** |

### 3. Model Architecture

| Component | Description | Key Strategy |
| :--- | :--- | :--- |
| **Base Model** | **MobileNetV2** | Pretrained on **ImageNet**. Used as a high-performance feature extractor. Initial layers are **frozen** to retain learned representations. |
| **Classification Head** | Global Average Pooling, Dense Layer(s), **Softmax** Layer | Custom layers built on top of the backbone for multi-class disease discrimination. |

## 📊 **Results & Interpretation**

The MobileNetV2-based classifier demonstrates strong pattern recognition capability and high adaptability.

* **Robustness:** Stable accuracy improvement and smooth learning curves achieved due to the **Transfer Learning** approach.
* **Efficiency:** The model is computationally *lightweight*, affirming its suitability for deployment in **mobile telemedicine** or diagnostic assistance systems.
* **Discrimination:** The architecture effectively uses low-level features (edges, textures) from the backbone and high-level features from fine-tuning to discriminate between different skin conditions.

## 📂 **Project Structure**
