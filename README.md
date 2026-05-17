<h1 align="center">Plant-Leaf-Disease-Detection-System</h1>
Deep learning pipeline for potato leaf disease classification (early blight, late blight) | CNN trained on 2,152 images with data augmentation | 97.26% accuracy | TensorFlow · Keras · Scikit-learn · Saturn Cloud


## Problem Statement
Potato crops are highly vulnerable to fungal diseases like Early Blight and Late Blight, which can devastate entire harvests if not detected early. Manual identification requires agricultural expertise that many small-scale farmers lack. This project automates disease detection from leaf images using deep learning — enabling early intervention and reducing crop loss.

## Key Results
| Metric | Value |
|---|---|
| Model Accuracy | **97.26%** |
| Dataset Size | 2,152 images |
| Image Resolution | 256 × 256 px |
| Train / Test Split | 80 : 20 |
| Batch Size | 32 |
| Classes | Early Blight, Late Blight, Healthy |

## How It Works

```
Input Image (Leaf Photo)
        ↓
Preprocessing (Resize → Normalize → Augment)
        ↓
CNN Model (TensorFlow + Keras)
        ↓
Prediction: Early Blight / Late Blight / Healthy
        ↓
Confidence Score Output
```


## Dataset
- **Source:** [PlantVillage Dataset](https://www.kaggle.com/datasets/arjuntejaswi/plant-village)
- **Classes:** Early Blight, Late Blight, Healthy
- **Total Images:** 2,152 potato leaf images
- **Split:** 80% training / 20% testing
- **Platform:** Saturn Cloud (cloud-based training environment)

## Model Architecture

- **Type:** Convolutional Neural Network (CNN)
- **Framework:** TensorFlow + Keras
- **Input Shape:** (256, 256, 3)
- **Batch Size:** 32

### Techniques Used
- Data Augmentation (flipping, rotation, zoom) to reduce overfitting
- Hyperparameter tuning for optimal learning rate and epochs
- Train/test split for unbiased evaluation
- Model evaluation using accuracy and loss curves

---

## Results

| Class | Description |
|---|---|
| **Early Blight** | Caused by *Alternaria solani* — brown spots with yellow rings |
| **Late Blight** | Caused by *Phytophthora infestans* — dark, water-soaked lesions |
| **Healthy** | No disease detected |

Training achieved **97.26% accuracy** on the test set through data augmentation and hyperparameter tuning.

---

## Project Screenshots

<img width="1901" height="1016" alt="Screenshot 2024-05-11 144320" src="https://github.com/user-attachments/assets/f1566b56-2032-46a8-b281-3b280fc32e9c" />

<img width="1870" height="827" alt="Screenshot 2024-05-11 144430" src="https://github.com/user-attachments/assets/44316599-f870-42b3-814d-40710bfc0334" />



## Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| TensorFlow | Model training and evaluation |
| Keras | Model design and layer architecture |
| Scikit-learn | Metrics and model evaluation |
| NumPy / Pandas | Data manipulation |
| Matplotlib | Visualising training curves |
| Saturn Cloud | Cloud-based GPU training environment |


---

## Future Improvements

- [ ] Expand to more crop types (tomato, corn, wheat)
- [ ] Build a Flask or Streamlit web interface for farmer use
- [ ] Deploy on Hugging Face Spaces for public access
- [ ] Add Grad-CAM visualisation to highlight diseased regions
- [ ] Integrate with a mobile app for field use


