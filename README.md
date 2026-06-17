<h1 align="center">Plant-Leaf-Disease-Detection-System</h1>
Deep learning pipeline for potato leaf disease classification (early blight, late blight) | CNN trained on 2,152 images with data augmentation | 97.26% accuracy | TensorFlow · Keras · Scikit-learn · Saturn Cloud

[![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat-square&logo=tensorflow)](https://tensorflow.org)
[![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?style=flat-square&logo=keras)](https://keras.io)
[![Gradio](https://img.shields.io/badge/Gradio-HuggingFace-yellow?style=flat-square&logo=huggingface)](https://huggingface.co)
[![Accuracy](https://img.shields.io/badge/Accuracy-97.26%25-brightgreen?style=flat-square)]()
[![Saturn Cloud](https://img.shields.io/badge/Trained%20on-Saturn%20Cloud-purple?style=flat-square)]()

[Live Demo](https://huggingface.co/spaces/adarshgupta1200/Plant-Leaf-Disease-Detection-System) • [Architecture](#how-it-works) • [Getting Started](#getting-started)

## Problem Statement
Potato crops are highly vulnerable to fungal diseases like Early Blight and Late Blight, which can devastate entire harvests if not detected early. Manual identification requires agricultural expertise that many small-scale farmers lack. This project automates disease detection from leaf images using deep learning — enabling early intervention and reducing crop loss.


## Key Results
| Metric | Value |
|--------|-------|
| Model Accuracy | **97.26%** |
| Dataset Size | 2,152 potato leaf images |
| Image Resolution | 256 × 256 px |
| Train / Test Split | 80 : 20 |
| Batch Size | 32 |
| Classes | Early Blight, Late Blight, Healthy |
| Training Platform | Saturn Cloud (GPU) |
| Public Demo | Gradio on Hugging Face Spaces |


## How It Works

### Training Pipeline

```
Input Image (Potato Leaf Photo)
        │
        ├── Resize to 256×256
        ├── Normalize pixel values
        └── Data Augmentation (flip, rotate, zoom)
        │
        ▼
CNN Model (TensorFlow + Keras)
        │
        ▼
Prediction: Early Blight / Late Blight / Healthy
        │
        ▼
Confidence Score Output
```

### Hugging Face Spaces (Gradio)

```
User uploads leaf image (Gradio UI)
        │
        ├── Extract saved_model.zip (first run only)
        ├── Auto-detect saved_model.pb path
        └── Load model via tf.saved_model signatures
        │
        ▼
predict() function
        ├── Resize + normalize image
        ├── CNN inference → class probabilities
        └── Grad-CAM (GradientTape on input tensor)
                └── Heatmap overlay on original image
        │
        ▼
Gradio displays:
  ├── Prediction label with confidence bars (3 classes)
  └── Grad-CAM heatmap with colour legend
```

---

## Disease Classes

| Class | Pathogen | Visual Signs |
|-------|----------|-------------|
| **Early Blight** | *Alternaria solani* (fungus) | Brown spots with concentric yellow rings |
| **Late Blight** | *Phytophthora infestans* (oomycete) | Dark, water-soaked lesions spreading rapidly |
| **Healthy** | — | No disease detected |

Late Blight is the more dangerous of the two — it spreads faster, is harder to treat, and under humid conditions can destroy an entire field within a week.

---

## Dataset
- **Source:** [PlantVillage Dataset](https://www.kaggle.com/datasets/arjuntejaswi/plant-village)
- **Classes:** Early Blight, Late Blight, Healthy
- **Total Images:** 2,152 potato leaf images
- **Split:** 80% training / 20% testing
- **Platform:** Saturn Cloud (cloud-based training environment)


## Model Architecture

```
Input (256×256×3)
        │
        ├── Conv2D → ReLU → MaxPooling  (repeated blocks)
        │
        ├── Flatten
        ├── Dense (fully connected)
        └── Dense → Softmax (3 classes)
```

**Grad-CAM implementation** — during inference, `tf.GradientTape` records the gradient of the predicted class score with respect to the input image pixels. The gradients are collapsed across colour channels by taking the maximum absolute value, producing a spatial importance map. A Gaussian blur is applied for a cleaner visual, and the result is upsampled to the original 256×256 size and overlaid on the leaf image with a JET colormap.


## Techniques Used
- Data Augmentation (flipping, rotation, zoom) to reduce overfitting
- Hyperparameter tuning for optimal learning rate and epochs
- Train/test split for unbiased evaluation
- Model evaluation using accuracy and loss curves

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| TensorFlow + Keras | Model training, inference, and SavedModel export |
| Scikit-learn | Metrics and model evaluation |
| NumPy / Pandas | Data manipulation and preprocessing |
| Matplotlib | Training curve visualisation |
| OpenCV | Grad-CAM heatmap generation and overlay |
| Gradio | Web interface for public demo |
| Hugging Face Spaces | Public deployment and hosting |
| Saturn Cloud | Cloud GPU training environment |

---

## Results

| Class | Description |
|---|---|
| **Early Blight** | Caused by *Alternaria solani* — brown spots with yellow rings |
| **Late Blight** | Caused by *Phytophthora infestans* — dark, water-soaked lesions |
| **Healthy** | No disease detected |

Training achieved **97.26% accuracy** on the test set through data augmentation and hyperparameter tuning.


## Project Screenshots

<img width="1901" height="1016" alt="Screenshot 2024-05-11 144320" src="https://github.com/user-attachments/assets/f1566b56-2032-46a8-b281-3b280fc32e9c" />

<img width="1870" height="827" alt="Screenshot 2024-05-11 144430" src="https://github.com/user-attachments/assets/44316599-f870-42b3-814d-40710bfc0334" />

## Getting Started

### Prerequisites

```bash
pip install tensorflow keras scikit-learn numpy pandas matplotlib opencv-python
```

### Clone the Repository

```bash
git clone https://github.com/adarsh288/plant-leaf-disease-detection.git
cd plant-leaf-disease-detection
```

### Run the Training Notebook

```bash
jupyter notebook Plant_Disease_Detection.ipynb
```

App starts at `http://localhost:7860`

---

## Future Improvements

- [ ] Expand to more crop types (tomato, corn, wheat)
- [ ] Add LLM explanation layer for plain-English disease descriptions
- [ ] Integrate with a mobile app for field use
- [ ] Add severity scoring alongside classification
- [ ] Support real-time detection via device camera

---

## Disclaimer

> This tool is intended for educational and research purposes. It is not a substitute for professional agricultural diagnosis. Always consult a qualified agronomist or plant pathologist before making crop management decisions.



