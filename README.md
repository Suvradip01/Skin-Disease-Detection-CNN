# 🩺 AI-Based Skin Disease Detection using MobileNetV2

## **A Deep Learning Approach for Automated Dermatological Image Classification**

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-2.x-red.svg)](https://keras.io/)

---

## 🧭 **Introduction**

Skin diseases affect millions globally, and timely diagnosis is critical for effective treatment. However, access to specialist dermatologists is often limited, particularly in remote and underserved areas.

This project introduces a **lightweight and efficient deep-learning-based solution** for automated skin disease classification. By leveraging **MobileNetV2**—an architecture optimized for mobile and low-resource environments—the goal is to create a highly accurate, yet computationally efficient, diagnostic assistance system suitable for deployment on mobile devices or in basic clinic settings.

---

## 🎯 **Research Objectives**

* Develop a **reliable machine learning system** for classifying multiple skin disease categories from image data.
* Utilize **transfer learning** with a **MobileNetV2** backbone to accelerate model convergence and ensure robust feature extraction.
* Evaluate performance rigorously using standard training/validation metrics and visualizations.
* Establish a **structured and reproducible workflow** for easy future expansion and experimentation.

---

## 🧠 **Methodology**

### **1. Dataset Preparation**

The dataset is structured into folders, where each folder represents an individual skin disease class.

| Aspect | Detail | Tool/Method |
| :--- | :--- | :--- |
| **Data Source** | Images organized into class-specific folders (`dataset/`). | Custom |
| **Data Loading** | Handles file loading, resizing, batch creation, shuffling, and label generation. | `tf.keras.preprocessing.image_dataset_from_directory()` |
| **Preprocessing** | All images are standardized to a consistent size. | $190 \times 190$ |
| **Labeling** | Labels are dynamically determined from the folder names. | **Categorical** |

### **2. Configuration & Training Details**

| Setting | Value | Rationale |
| :--- | :--- | :--- |
| **Input Image Size** | **$190 \times 190 \times 3$** | Standardized input for the CNN. |
| **Batch Size** | **16** | Optimizes memory usage and training speed. |
| **Epochs** | **50** | The intended full training duration. |
| **Loss Function** | **Sparse Categorical Crossentropy** | Suitable for multi-class classification with integer labels. |
| **Optimizer** | **Adam** | A highly effective, adaptive optimization algorithm. |

### **3. Model Architecture: Hybrid Transfer Learning**

The core of the system is a hybrid model leveraging the power and efficiency of a pre-trained CNN.

| Component | Architecture | Purpose |
| :--- | :--- | :--- |
| **Base Model** | **MobileNetV2** (Pretrained on **ImageNet**) | Acts as a high-performance, efficient feature extractor. Initial layers are **frozen** to retain learned representations. |
| **Custom Head** | Global Average Pooling, Dense Layer(s), **Softmax** Output | Adapts the extracted features to the specific task of multi-class skin disease classification. |

### **4. Evaluation**

The notebook includes detailed visualizations to monitor learning dynamics and potential overfitting:
* Training vs. validation **accuracy plots**.
* Training vs. validation **loss plots**.
* Sample predictions and class detection verification.

---

## 📊 **Results & Interpretation**

The **MobileNetV2**-based classifier demonstrates strong pattern recognition capability and high adaptability.

* **Robust Feature Extraction:** The pre-trained layers provide robust low-level feature extraction, resulting in smooth and **stable learning curves**.
* **Deployment Suitability:** The choice of **MobileNetV2** ensures the model remains computationally **lightweight**, making it highly suitable for mobile telemedicine tools or low-resource deployments.

---

## 🛠️ **Technologies Used**

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Core Language** | **Python 3** | The core programming language for development. |
| **Deep Learning** | **TensorFlow** / **Keras** | Framework for model development, training, and evaluation. |
| **Model Backbone**| **MobileNetV2** | The efficient CNN used for feature extraction. |
| **Visualization** | **Matplotlib** | Generating training/validation plots and prediction visualizations. |
| **Environment** | **Jupyter Notebook** | Environment for running the `MobileNetV2.ipynb` workflow. |

---

## ▶️ **How to Use & Project Structure**

### **1. Project Structure**

AI-Skin-Disease-Detection/ │ ├── MobileNetV2.ipynb # 💻 Notebook containing all model building, training, and evaluation code. └── dataset/ # 🖼️ Image dataset organized by individual classes. ├── class_1/

├── class_2/

└── ...


### **2. Prerequisites**

You must have **Python 3** installed, along with the following libraries:

```bash
# Install the required libraries via pip
pip install tensorflow matplotlib jupyter
3. Setup Instructions
Clone the repository:

Bash

git clone [Your Repository URL]
cd AI-Skin-Disease-Detection
Organize your dataset: Place your skin disease images into the required class-separated directory structure inside the dataset/ folder.

dataset/
   ├── classA/
   ├── classB/
   └── classC/
Run the notebook:

Bash

jupyter notebook MobileNetV2.ipynb
Execute Cells: Step through the notebook cells sequentially to load the dataset, build the MobileNetV2 model, start the 50-epoch training process, and finally generate the evaluation plots and sample predictions.

🔍 Future Work
To enhance the performance and reliability of this system, future developments may include:

Data Augmentation: Implement advanced techniques (rotation, zoom, contrast adjustments) to improve model generalization.

Deeper Fine-Tuning: Unfreeze and fine-tune deeper MobileNetV2 layers.

Alternative Architectures: Evaluate alternative efficient architectures, such as EfficientNet or MobileNetV3.

Deployment: Export the model to TensorFlow Lite for native mobile application integration.

End-User Interface: Building a user-friendly diagnostic assistance interface.

📜 License
This project is licensed under the ISC License, allowing free use, modification, and distribution with attribution.

🙌 Acknowledgements
We thank Google Research for the creation of MobileNetV2, the TensorFlow/Keras community for their excellent framework, and the providers of the dermatology datasets used for experimentation.
