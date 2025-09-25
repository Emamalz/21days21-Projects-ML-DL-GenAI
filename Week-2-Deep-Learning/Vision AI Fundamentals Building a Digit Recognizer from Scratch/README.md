# CIFAR-100 Image Classification

## Overview
This project applies deep learning techniques to classify images from the CIFAR-100 dataset.  
The dataset contains 60,000 color images across 100 classes, with 50,000 for training and 10,000 for testing.  
The goal is to compare how model complexity (ANN vs Basic CNN vs Deeper CNN) affects performance on this challenging dataset.

---

## Dataset
- Training set: 50,000 images
- Test set: 10,000 images
- Image size: 32x32x3 (RGB color)
- Number of classes: 100

### Preprocessing
- Normalized pixel values to [0,1]
- One-hot encoded labels
- No reshape required (data already in shape (32,32,3))

---

## Models

### Artificial Neural Network (ANN)
- Flatten → Dense(512, ReLU) → Dropout  
- Dense(256, ReLU) → Dropout  
- Dense(100, Softmax)

### Basic CNN
- Conv2D(32) → MaxPooling → Dropout  
- Conv2D(64) → MaxPooling → Dropout  
- Flatten → Dense(256, ReLU) → Dropout → Dense(100, Softmax)

### Deeper CNN
- Multiple Conv2D layers (32 → 64 → 128) with BatchNorm and Dropout  
- MaxPooling layers for downsampling  
- Dense(256, ReLU) → Dropout  
- Dense(100, Softmax)

---

## Training
- Optimizer: Adam  
- Loss: Categorical Crossentropy  
- Metric: Accuracy  
- Callbacks:
  - EarlyStopping (patience=5, restore best weights)
  - ModelCheckpoint (save best weights)

---

## Results

| Model       | Test Accuracy | Test Loss |
|-------------|---------------|-----------|
| ANN         | ~0.22         | ~3.25     |
| Basic CNN   | ~0.20         | ~3.36     |
| Deeper CNN  | ~0.30–0.40    | Lower than ANN and Basic CNN |

- ANN provides a weak baseline.
- Basic CNN shows improvements due to convolutional feature extraction.
- Deeper CNN performs best, though training is more computationally expensive.

---

## Visualizations
- Training histories (accuracy and loss curves)
- Bar charts comparing model accuracy and loss
- Confusion matrices (full 100x100 and zoomed subsets for readability)
- Prediction grids showing correct (green) and incorrect (red) classifications

---

## Conclusion
Model complexity directly impacts performance on CIFAR-100.  
The ANN was insufficient for such a complex dataset, while CNNs provided better performance by capturing spatial and color features.  
The deeper CNN achieved the strongest results, confirming that more advanced architectures are better suited for CIFAR-100.  

Future improvements could include data augmentation, hyperparameter tuning, or transfer learning with pretrained models such as ResNet or DenseNet.
