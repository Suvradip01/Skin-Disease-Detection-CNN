# 🩺 AI-Based Skin Disease Detection using MobileNetV2

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Keras](https://img.shields.io/badge/Keras-API-red)

## 📌 Project Overview

This project leverages **Deep Learning** and **Transfer Learning** to automate the detection and classification of skin diseases. Utilizing the **MobileNetV2** architecture—a state-of-the-art, lightweight convolutional neural network—the model is designed to be efficient enough for deployment on mobile and edge devices while maintaining high diagnostic accuracy.

The system classifies skin lesions into **3 distinct categories**:
1. **Benign**
2. **Melanoma** (Malignant)
3. **Non-Melanoma Cancer**

---

## 🧠 Model Architecture & Methodology

### Why MobileNetV2?
We selected **MobileNetV2** as the backbone for this project due to its superior balance between latency and accuracy. It introduces two key architectural innovations:
* **Inverted Residuals:** These allow the network to preserve information more effectively by connecting bottlenecks.
* **Linear Bottlenecks:** This prevents non-linearities (like ReLU) from destroying information in low-dimensional manifolds.

### Transfer Learning Strategy
Instead of training a deep network from scratch (which requires massive datasets and compute power), we utilized **Transfer Learning**:
1.  **Pre-trained Backbone:** We utilized MobileNetV2 pre-trained on the **ImageNet** dataset (1.4M images) to extract robust features (edges, textures, patterns).
2.  **Custom Head:** The top classification layers of MobileNetV2 were removed and replaced with a custom dense neural network tailored to our 3 classes.
3.  **Fine-Tuning:** Initially, the backbone layers were frozen. In later stages, specific layers were unfrozen and trained with a lower learning rate to adapt the model specifically to dermatological textures.

---

## 📂 Dataset Structure

The model expects the dataset to be organized in a standard directory format suitable for `image_dataset_from_directory`:

dataset/ ├── benign/ # Images of benign skin lesions ├── melanoma/ # Images of malignant melanoma └── non_melanoma_cancer/ # Images of other skin cancers


* **Total Images:** ~3,600 files
* **Classes:** 3
* **Input Shape:** `(190, 190, 3)`

---

## ⚙️ Configuration & Training Parameters

The training pipeline is optimized with the following hyperparameters extracted from the project code:

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **Base Model** | MobileNetV2 | Pre-trained on ImageNet |
| **Input Shape** | 190 x 190 px | Resolution resized for the model |
| **Batch Size** | 16 | Number of images processed per step |
| **Epochs** | 50 | Maximum training iterations |
| **Optimizer** | Adam | Adaptive learning rate optimization |
| **Loss Function** | Sparse Categorical Crossentropy | For integer-encoded labels |
| **Callbacks** | EarlyStopping, ReduceLROnPlateau | Prevents overfitting & optimizes learning rate |

---

## 🚀 Installation & Usage

### Clone the Repository
```bash
git clone [https://github.com/yourusername/skin-disease-detection.git](https://github.com/yourusername/skin-disease-detection.git)
cd skin-disease-detection
2. Install Dependencies
Ensure you have Python installed, then install the required libraries:

Bash

pip install tensorflow matplotlib numpy
3. Prepare Data
Place your image dataset folder (e.g., Diseases) in the root directory. Ensure it follows the folder structure mentioned above.

4. Run the Notebook
Launch Jupyter Notebook and open the project file:

Bash

jupyter notebook MobileNetV2.ipynb
Execute the cells sequentially to load data, build the model, and start training.

📊 Performance & Results
The model employs advanced training techniques including Learning Rate Reduction and Early Stopping to achieve optimal convergence.

Training Accuracy: ~83%

Validation Accuracy: ~78%

Test Accuracy: ~77.5%

Note: The model saves the best weights automatically to best_model.keras based on validation loss minimization.

Visualizing Predictions
The notebook includes code to visualize predictions on unseen test data, displaying the actual class versus the predicted class with confidence scores.

🛠️ Technology Stack
Language: Python 3

Deep Learning: TensorFlow, Keras

Data Processing: NumPy, tf.data API

Visualization: Matplotlib

🔮 Future Work
Data Augmentation: Implement advanced augmentation (CutMix, MixUp) to improve generalization and handle class imbalance.

Quantization: Convert the model to TensorFlow Lite (TFLite) for deployment on Android/iOS mobile apps.

Explainability: Integrate Grad-CAM to visualize which parts of the skin lesion the model focuses on for diagnosis.

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
