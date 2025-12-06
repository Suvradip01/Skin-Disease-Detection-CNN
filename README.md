# 🩺 AI-Based Skin Disease Detection using MobileNetV2

## **A Deep Learning Approach for Automated Dermatological Image Classification**

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)

---

## 🧭 **Introduction**

Skin diseases affect millions globally, and timely diagnosis is critical for effective treatment. However, access to specialist dermatologists is often limited, particularly in remote and underserved areas.

This project introduces a **lightweight and efficient deep-learning-based solution** for automated skin disease classification. By leveraging **MobileNetV2**—an architecture optimized for mobile and low-resource environments—the goal is to create a highly accurate, yet computationally efficient, diagnostic assistance system suitable for deployment on mobile devices or in basic clinic settings.

---

## 🎯 **Research Objective**

* Develop a **reliable machine learning system** for classifying multiple skin disease categories from image data.
* Utilize **transfer learning** with a MobileNetV2 backbone to accelerate model convergence and ensure robust feature extraction.
* Evaluate performance rigorously using standard training/validation metrics and visualizations.
* Establish a **structured and reproducible workflow** for easy future expansion and experimentation.

---

## 🧠 **Methodology**

### **Model Architecture: Hybrid Transfer Learning**

The core of the system is a hybrid model leveraging the power and efficiency of a pre-trained CNN.

| Component | Architecture | Purpose |
| :--- | :--- | :--- |
| **Base Model** | **MobileNetV2** (Pretrained on ImageNet) | Acts as a high-performance, efficient feature extractor. Initial layers are **frozen** to preserve learned, low-level representations. |
| **Custom Head** | Global Average Pooling, Dense Layer(s), Softmax Output | Adapts the extracted features to the specific task of multi-class skin disease classification. |

### **Configuration & Training Details**

| Setting | Value |
| :--- | :--- |
| **Input Image Size** | $190 \times 190 \times 3$ |
| **Batch Size** | 16 |
| **Epochs** | 50 |
| **Loss Function** | Sparse Categorical Crossentropy |
| **Optimizer** | Adam |
| **Data Loading** | `tf.keras.preprocessing.image_dataset_from_directory()` for efficient loading, resizing, and batching. |

### **Evaluation**

The system's performance is monitored through **accuracy and loss curves** (Training vs. Validation) to visually inspect learning dynamics, stability, and identify potential overfitting.

---

## 📊 **Results & Interpretation**

The MobileNetV2-based classifier demonstrates **strong capability** in discerning complex skin disease patterns.

* **Robust Feature Extraction:** The pre-trained MobileNetV2 layers efficiently extract fundamental features (edges, textures, shapes), leading to smooth and stable learning curves.
* **High Adaptability:** The transfer learning approach shows good potential for building scalable diagnostic assistance systems, even when adapting to a limited, domain-specific dataset.
* **Deployment Suitability:** The use of MobileNetV2 ensures the model remains computationally lightweight, making it highly suitable for mobile telemedicine tools or low-resource deployments.

---

## 🛠️ **Technologies Used**

* **Core Language:** Python 3
* **Deep Learning Framework:** TensorFlow / Keras
* **Backbone:** MobileNetV2
* **Visualization:** Matplotlib

---

## ▶️ **How to Use & Project Structure**

### **Prerequisites**

You must have Python 3 and the following libraries installed:

```bash
pip install tensorflow matplotlib
