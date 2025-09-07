# VGG16-Classifier
This project demonstrates the use of transfer learning with a pretrained VGG16 model to classify images from the Fashion-MNIST dataset.

## 📝 Overview

Dataset: Fashion-MNIST (28x28 grayscale images of clothing).

Goal: Predict 1 of 10 fashion categories.

Approach: Transfer learning with VGG16 pretrained on ImageNet.

## 📊 Results (6 epochs)
Metric	Value
Training Accuracy	~99%
Test Accuracy	~93%
Loss (last epoch)	~0.078

Using VGG16 allowed the model to leverage rich feature representations learned from ImageNet, improving accuracy compared to training from scratch.

## 🛠️ Preprocessing & Transformations

Scaling: Pixel values normalized to [0, 1] for faster convergence.

Resizing & Cropping: Images resized to 256x256 and center-cropped to 224x224 to match VGG16 input size.

RGB Conversion: Original grayscale images converted to 3-channel RGB for compatibility with VGG16.

Normalization: Standard ImageNet mean & std applied ([0.485, 0.456, 0.406] and [0.229, 0.224, 0.225]).

These steps ensure the small Fashion-MNIST images are compatible with the pretrained VGG16 model and leverage learned features from ImageNet.

## ⚡ Model & Training

VGG16: Frozen convolutional layers to reuse pretrained features.

Custom Classifier:
  Linear(25088 → 1024) → ReLU → Dropout(0.5)
  Linear(1024 → 512) → ReLU → Dropout(0.4)
  Linear(512 → 10)
Loss: CrossEntropyLoss

Optimizer: Adam

Epochs: 10

