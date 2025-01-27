# Artificial Fingerprints in DeepFake Detection

This project explores the use of **Artificial Fingerprints**—visible artifacts and anomalous patterns in the Fourier domain—as a method to classify real and fake images. By leveraging these fingerprints, the model aims to improve the detection of DeepFake content.

---

## What Are Artificial Fingerprints?
- **Definition**: Visible artifacts and anomalous regular patterns observed in the Fourier domain.
- Inspired by the paper: *"Intriguing properties of synthetic images: from generative adversarial networks to diffusion models."*

---

## Dataset
The project utilizes a balanced dataset consisting of **32,500 images** divided into real and fake categories:
- **Real Images**: CelebA, FFHQ.
- **Fake Images**: AttGAN, StarGAN, StyleGAN.

---

## Computational Resources
- The project was executed on **Google Colaboratory** with limited RAM and GPU.
- **Optimizations**:
  - Limited dataset size.
  - Training on a few epochs with **early stopping** to avoid overfitting.
  - Image resizing to **224x224 pixels** for efficient computation.

---

## Model Architectures

### 1. **ResNet18**
- **Not pre-trained**.
- Modified last layer for binary classification.

### 2. **Xception**
- Based on **Depthwise Separable Convolutions**.
- **Not pre-trained**.
- Modified last layer for binary classification.

### 3. **Custom Architecture**
- Combines two pipelines for:
  - **Image-based features**.
  - **Power spectrum features** (Fourier domain).
- Key components:
  - 5x5 convolutional layers with ReLU and Batch Normalization.
  - Dense layers with dropout.
  - **Concatenation** of image and power spectrum layers.
  - Sigmoid activation for final classification.

---

## Training and Experiments
- **Optimizer**: Adam, SGD.
- **Learning Rates**:
  - 0.01, 0.001, 0.0001, 0.000001.
- **Loss Function**: Binary Cross Entropy.
- **Dropout Probabilities**: 0.2, 0.3, 0.5.
- **Pooling Methods**: Max pooling and average pooling.

---

## Results

### Accuracy
- **ResNet18**: 0.847 (Image), 0.997 (Power Spectrum).
- **Xception**: 0.652 (Image), 0.990 (Power Spectrum).
- **Custom Model**: 0.861 (Image), 0.975 (Power Spectrum), **0.623 (Combined)**.

### Loss
- Custom Model combined accuracy demonstrated generalization across datasets:
  - **Real**: LSUN.
  - **Fake**: ProGAN.

---

## Future Work
- Improve GPU resources for training larger and more complex models.
- Expand dataset for better generalization across various DeepFake datasets.
