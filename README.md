# 🧠 CIFAR-10 Image Classification – Custom Neural Network with PyTorch

This project presents a custom-built convolutional neural network (CNN) designed to classify images from the **CIFAR-10** dataset. Developed as part of the **Neural Networks and Deep Learning (ECS7026P)** module at **Queen Mary University of London**, the model was carefully optimized to balance **performance, stability, and efficiency** — ultimately achieving **92% test accuracy**.

---

## 🎯 Objective

The goal was to design a deep learning model adhering to a constrained architectural framework, yet capable of outperforming standard baselines. Emphasis was placed on:
- Building intermediate blocks using **parallel convolutional branches** with learned weights
- Preventing overfitting through **smart regularization**
- Employing **training best practices** like OneCycle learning rate scheduling

---

## ✅ What I Built

A neural network that classifies 32x32 color images into one of 10 object classes, such as airplanes, cars, animals, etc. The project uses:
- **Custom intermediate blocks** with 4 parallel convolutional layers
- **Attention-based weighting** to combine features dynamically
- A lightweight yet powerful design focused on generalization

---

## ⚙️ How It Works

### 🔧 Architecture Highlights:
- **Three Intermediate Blocks**:
  - Each block has 4 conv layers receiving the same input.
  - Outputs are weighted and summed using coefficients from a small fully connected layer based on input stats.
  - Batch Normalization + ReLU + SEBlock included in each path.
- **Output Block**:
  - Global Average Pooling → Dense Layer → 10-class logits
- **Regularization & Enhancements**:
  - **SE Blocks** (Squeeze-and-Excitation) to emphasize relevant channels
  - **Stochastic Depth** (10% chance to drop blocks during training)
  - **Label Smoothing** (ε = 0.1)
  - **Data Augmentation**: Random flips, crops, rotations, color jitter

### 🧪 Training Details:
- **Optimizer:** AdamW (weight decay = 5e-4)
- **Learning Rate:** OneCycleLR (0.001 → 0.01 → 0.001)
- **Epochs:** 65
- **Batch Size:** 128
- **Loss Function:** CrossEntropyLoss with smoothing

---

### 📊 Visual Insights
- `accuracy_curve.png`: Shows consistent accuracy growth over epochs
- `loss_curve.png`: Smooth loss decline over training
- `confusion_matrix.png`: (Optional) Highlights strong classification across all 10 classes

---

## 🧠 What I Learned

- Architectural design matters — **how you combine features** can be more impactful than model depth.
- **Regularization techniques** like stochastic depth and label smoothing can drastically improve generalization.
- **Learning rate strategies** (e.g. OneCycle) speed up convergence and improve performance.
- Data augmentation isn't just a bonus — it's critical on small datasets like CIFAR-10.
