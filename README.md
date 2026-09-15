# Computer Vision with PyTorch

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-ee4c2c?logo=pytorch)
![Dataset](https://img.shields.io/badge/Dataset-FashionMNIST-black)
![Task](https://img.shields.io/badge/Task-Image%20Classification-green)

## Overview

This project is a hands-on implementation of **computer vision with PyTorch** using the FashionMNIST dataset.

The main goal was to build and compare different neural network architectures and understand why **CNNs are better suited for image data** than simple fully connected networks.

I trained three models:

- **Model 0** → Simple fully connected neural network
- **Model 1** → Fully connected network with ReLU
- **Model 2** → Convolutional Neural Network

The best model was the CNN, which reached **89.31% test accuracy**.

---

## Dataset

The project uses **FashionMNIST**, a dataset containing grayscale images of clothing items.

- Training samples: **60,000**
- Test samples: **10,000**
- Image size: **28 × 28**
- Channels: **1 (grayscale)**
- Classes: **10**

### Classes

`T-shirt/top` · `Trouser` · `Pullover` · `Dress` · `Coat` · `Sandal` · `Shirt` · `Sneaker` · `Bag` · `Ankle boot`

---

## Project Workflow

```text
FashionMNIST
     ↓
Data Exploration
     ↓
Tensor Conversion
     ↓
DataLoaders
     ↓
Model 0 — Fully Connected
     ↓
Model 1 — Fully Connected + ReLU
     ↓
Model 2 — CNN
     ↓
Model Comparison
     ↓
Predictions
     ↓
Confusion Matrix
     ↓
Save Model
     ↓
Load Model
     ↓
Verify Performance
```

---

## Models

### Model 0 — Baseline

The first model is a simple fully connected neural network.

```text
28 × 28
  ↓
Flatten
  ↓
Linear(784 → 10)
  ↓
Linear(10 → 10)
```

**Result**

- Test Accuracy: **83.43%**
- Test Loss: **0.477**
- Training Time: **47.16 s**

This model provides a baseline for comparing more advanced architectures.

---

### Model 1 — Fully Connected + ReLU

The second model adds ReLU activation functions to the fully connected network.

```text
Flatten
  ↓
Linear
  ↓
ReLU
  ↓
Linear
  ↓
ReLU
```

**Result**

- Test Accuracy: **84.92%**
- Test Loss: **0.434**
- Training Time: **365.49 s**

The improvement over Model 0 is relatively small despite the much longer training time.

---

### Model 2 — CNN

The final model uses convolutional layers, ReLU activations, and max pooling.

```text
Input
  ↓
Conv2D
  ↓
ReLU
  ↓
Conv2D
  ↓
ReLU
  ↓
MaxPool
  ↓
Conv2D
  ↓
ReLU
  ↓
Conv2D
  ↓
ReLU
  ↓
MaxPool
  ↓
Flatten
  ↓
Linear
  ↓
10 Classes
```

**Result**

- Test Accuracy: **89.31%**
- Test Loss: **0.314**
- Training Time: **574.20 s**

The CNN clearly outperformed both fully connected models.

---

## Model Comparison

| Model | Architecture | Test Accuracy | Test Loss | Training Time |
|---|---|---:|---:|---:|
| Model 0 | Fully Connected | 83.43% | 0.477 | 47.16 s |
| Model 1 | FC + ReLU | 84.92% | 0.434 | 365.49 s |
| **Model 2** | **CNN** | **89.31%** | **0.314** | 574.20 s |

### What I learned from the comparison

The CNN achieved the best performance because convolutional layers can learn useful **spatial patterns** from images.

A fully connected network receives flattened pixels and does not explicitly preserve the 2D structure of the image.

The CNN therefore provides a better inductive bias for this type of problem.

---

## Evaluation

The final CNN was evaluated using:

- Test loss
- Test accuracy
- Individual image predictions
- Prediction visualization
- Confusion matrix

The confusion matrix is particularly useful for identifying classes that the model commonly confuses, such as visually similar clothing categories.

---

## Model Saving & Loading

The trained CNN is saved using its PyTorch `state_dict`:

```text
models/
└── pytorch_computer_vision_model_2.pth
```

The notebook then recreates the same architecture, loads the saved weights, and evaluates the loaded model.

The loaded model reproduces the same recorded performance:

**89.31% test accuracy**

---

## Tech Stack

- Python
- PyTorch
- Torchvision
- TorchMetrics
- Matplotlib
- Pandas
- MLxtend
- tqdm

---

## Key Concepts Practiced

- FashionMNIST
- Tensor shapes
- Image visualization
- DataLoader
- Mini-batch training
- `nn.Module`
- `nn.Sequential`
- `nn.Flatten`
- `nn.Linear`
- `nn.ReLU`
- `nn.Conv2d`
- `nn.MaxPool2d`
- Cross Entropy Loss
- SGD optimizer
- Training and evaluation loops
- `model.train()`
- `model.eval()`
- `torch.inference_mode()`
- Softmax
- Argmax
- Confusion matrix
- Model `state_dict`
- Saving and loading PyTorch models

---

## What I Would Improve Next

Possible next steps:

- Tune the CNN architecture
- Experiment with different learning rates
- Compare Adam with SGD
- Add normalization
- Try data augmentation
- Increase/decrease the number of convolutional filters
- Add dropout or batch normalization
- Track training and validation curves
- Analyze the hardest-to-classify classes
- Test the model on custom clothing images

---

## Project Structure

```text
computer-vision/
│
├── computer_vision_model.ipynb
├── helper_functions.py
├── models/
│   └── pytorch_computer_vision_model_2.pth
└── README.md
```

---

## Conclusion

This project helped me move from basic neural networks to **CNN-based image classification** in PyTorch.

The main takeaway was simple:

> **For image data, the architecture matters.**

The fully connected models provided useful baselines, but the CNN was able to learn spatial features and improve test accuracy from **83.43% to 89.31%**.

This project is part of my ongoing learning journey in **Machine Learning, Deep Learning, and Artificial Intelligence**.

---

## Thanks for visiting! ⭐

If you found this project useful, consider giving the repository a **star**.

**Made with ❤️ while learning and building in Machine Learning, Deep Learning, and Artificial Intelligence.**
