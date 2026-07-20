# 🎯 ANN Cost (Loss) Function Cheat Sheet

> **Purpose:** A practical reference for selecting the appropriate cost (loss) function when training Artificial Neural Networks (ANNs).

---

# 📌 Quick Decision Guide

| If you're solving... | Output Activation | Recommended Loss |
|----------------------|-------------------|------------------|
| Regression | Linear | MSE |
| Regression (with Outliers) | Linear | Huber Loss |
| Regression (robust to Outliers) | Linear | MAE |
| Binary Classification | Sigmoid | Binary Cross-Entropy (BCE) |
| Multi-Class Classification | Softmax | Categorical Cross-Entropy (CCE) |
| Multi-Label Classification | Sigmoid | Binary Cross-Entropy (BCE) |
| Semantic Segmentation | Softmax / Sigmoid | Dice Loss / Cross-Entropy |
| Object Detection | Mixed Outputs | Focal Loss + IoU Loss |
| Imbalanced Classification | Sigmoid / Softmax | Focal Loss |

---

# 📊 Loss Function Comparison

| Loss Function | Typical Task | Error Behavior | Sensitive to Outliers | Recommended For |
|---------------|--------------|----------------|-----------------------|-----------------|
| **MSE** | Regression | Squares the error | ⭐⭐⭐ High | Numerical prediction |
| **MAE** | Regression | Absolute error | ⭐ Low | Robust regression |
| **Huber Loss** | Regression | MSE for small errors, MAE for large ones | ⭐⭐ Medium | Regression with noisy data |
| **Binary Cross-Entropy (BCE)** | Binary Classification | Probability error | N/A | Yes/No prediction |
| **Categorical Cross-Entropy (CCE)** | Multi-Class Classification | Probability distribution error | N/A | One correct class |
| **Sparse Categorical Cross-Entropy** | Multi-Class | Same as CCE using integer labels | N/A | Large datasets |
| **Focal Loss** | Imbalanced Classification | Focuses on difficult samples | N/A | Rare event detection |
| **Dice Loss** | Image Segmentation | Measures overlap | N/A | Medical imaging |
| **IoU Loss** | Object Detection | Measures box overlap | N/A | Bounding box prediction |

---

# 📖 Error Behavior

| Loss | Penalizes Large Errors? | Formula Style |
|------|-------------------------|---------------|
| **MSE** | ⭐⭐⭐ Strongly | Error² |
| **MAE** | ⭐ Equal | Absolute Error |
| **Huber** | ⭐⭐ Balanced | Hybrid |
| **BCE** | Probability Error | Logarithmic |
| **CCE** | Probability Distribution | Logarithmic |
| **Focal** | Hard Examples | Weighted BCE |
| **Dice** | Overlap | Similarity Score |
| **IoU** | Bounding Box Overlap | Intersection / Union |

---

# 🎯 Which Loss Should I Choose?

| Problem | Best Loss |
|----------|-----------|
| Predict House Price | ✅ MSE |
| Predict Temperature | ✅ MSE |
| Predict Sales | ✅ MSE |
| Stock Price Prediction | ✅ Huber |
| Binary Classification | ✅ Binary Cross-Entropy |
| Spam Detection | ✅ Binary Cross-Entropy |
| Fraud Detection | ✅ Binary Cross-Entropy / Focal Loss |
| Image Classification | ✅ Categorical Cross-Entropy |
| Handwritten Digit Recognition (MNIST) | ✅ Categorical Cross-Entropy |
| Multi-Label Image Tagging | ✅ Binary Cross-Entropy |
| Medical Image Segmentation | ✅ Dice Loss |
| Object Detection (YOLO, Faster R-CNN) | ✅ IoU + Focal Loss |

---

# 🌳 Decision Tree

```text
                    Start
                      │
             What is the task?
                      │
      ┌───────────────┼────────────────┐
      │               │                │
 Regression     Classification    Segmentation
      │               │                │
      │         ┌─────┴─────┐          │
      │         │           │          │
      │      Binary     Multi-Class    │
      │         │           │          │
      ▼         ▼           ▼          ▼
   MSE/MAE   BCE         CCE       Dice Loss
      │
      └───────────────┐
                      │
           Many Outliers?
               │
        ┌──────┴──────┐
        │             │
       Yes            No
        │             │
     Huber Loss      MSE
```

---

# ⚖️ Loss Function Characteristics

| Loss | Advantages | Drawbacks |
|------|------------|-----------|
| **MSE** | Smooth gradients, easy optimization | Very sensitive to outliers |
| **MAE** | Robust to outliers | Slower optimization |
| **Huber** | Best of MSE and MAE | Slightly more computation |
| **Binary Cross-Entropy** | Perfect for probabilities | Requires sigmoid output |
| **Categorical Cross-Entropy** | Excellent for multi-class problems | Requires softmax output |
| **Focal Loss** | Excellent for imbalanced data | Requires tuning γ (gamma) |
| **Dice Loss** | Great overlap metric | Mostly used in segmentation |
| **IoU Loss** | Optimizes bounding boxes directly | Detection-specific |

---

# 🔗 Activation Function Pairing

| Output Activation | Compatible Loss Function |
|-------------------|--------------------------|
| Linear | MSE / MAE / Huber |
| Sigmoid | Binary Cross-Entropy |
| Softmax | Categorical Cross-Entropy |
| Sigmoid (Multi-Label) | Binary Cross-Entropy |

---

# 🚀 Modern Best Practices (2026)

### Regression

- ✅ MSE for most regression tasks.
- ✅ Huber Loss when outliers exist.
- ✅ MAE when every error should have equal importance.

---

### Classification

- ✅ Binary Cross-Entropy for binary classification.
- ✅ Categorical Cross-Entropy for multi-class classification.
- ✅ Binary Cross-Entropy for multi-label classification.
- ✅ Focal Loss for highly imbalanced datasets.

---

### Computer Vision

- ✅ Dice Loss for segmentation.
- ✅ IoU Loss for object localization.
- ✅ Focal Loss for rare object detection.

---

# 🚀 One-Minute Summary

| Problem | Output | Loss |
|----------|--------|------|
| Regression | Linear | 🟢 MSE |
| Regression + Outliers | Linear | 🟢 Huber |
| Binary Classification | Sigmoid | 🟢 BCE |
| Multi-Class Classification | Softmax | 🟢 CCE |
| Multi-Label Classification | Sigmoid | 🟢 BCE |
| Segmentation | Softmax / Sigmoid | 🟢 Dice |
| Object Detection | Mixed | 🟢 Focal + IoU |

---

# 💡 Rule of Thumb

> **Regression**
>
> ➜ **MSE**
>
> ➜ **Huber** *(if outliers exist)*

> **Classification**
>
> - Binary → **Binary Cross-Entropy**
> - Multi-Class → **Categorical Cross-Entropy**
> - Multi-Label → **Binary Cross-Entropy**

> **Computer Vision**
>
> - Segmentation → **Dice Loss**
> - Object Detection → **IoU + Focal Loss**

---

# 🧠 Remember

> **Activation Function** decides **how neurons produce outputs**.

> **Loss Function** measures **how wrong the entire network is**.

> **Optimizer** (SGD, Adam, RMSprop...) uses the loss to update the network weights.

Together they form the learning loop:

```text
Input
   │
   ▼
Neurons
(Activation Functions)
   │
   ▼
Prediction
   │
   ▼
Loss Function
   │
   ▼
Backpropagation
   │
   ▼
Optimizer
   │
   ▼
Updated Weights
```