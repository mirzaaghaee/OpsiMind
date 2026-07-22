# 🧠 CNN (Convolutional Neural Network) Cheat Sheet

> A quick reference for understanding Convolutional Neural Networks (CNNs), their architecture, components, best practices, and potential applications in **Opsimind**.

---

# What is CNN?

A **Convolutional Neural Network (CNN)** is a deep learning architecture designed to process **grid-like data**, especially images.

Unlike a traditional Artificial Neural Network (ANN), CNN learns **local spatial patterns** such as edges, textures, and shapes using convolution operations.

Typical applications include:

- Image Classification
- Object Detection
- Image Segmentation
- OCR (Optical Character Recognition)
- Face Recognition
- Medical Imaging
- Video Analysis

---

# Why CNN?

Traditional ANN connects every input neuron to every hidden neuron.

```
Image (224×224×3)

↓

150,528 Inputs

↓

Fully Connected Layer
```

This creates millions of parameters.

CNN instead learns local patterns:

```
Image

↓

Convolution

↓

Pooling

↓

Convolution

↓

Pooling

↓

Dense Layers

↓

Prediction
```

Advantages:

- Far fewer parameters
- Faster training
- Better image understanding
- Preserves spatial information

---

# CNN Architecture

```
Input Image
      │
      ▼
Convolution
      │
      ▼
ReLU
      │
      ▼
Pooling
      │
      ▼
Convolution
      │
      ▼
ReLU
      │
      ▼
Pooling
      │
      ▼
Flatten
      │
      ▼
Dense Layer
      │
      ▼
Output
```

---

# Main Building Blocks

| Layer | Purpose |
|---------|----------|
| Input | Raw image |
| Convolution | Detect visual patterns |
| Activation (ReLU) | Introduce non-linearity |
| Pooling | Reduce image size |
| Batch Normalization | Stabilize training |
| Dropout | Prevent overfitting |
| Flatten | Convert feature maps into vector |
| Dense | Final prediction |
| Softmax | Multi-class probabilities |

---

# Convolution Layer

Instead of analyzing the whole image at once, CNN slides a small filter across the image.

Example kernel:

```
1 0 1
0 1 0
1 0 1
```

Output:

```
Image
   *
Kernel
   ↓
Feature Map
```

CNN automatically learns filters that detect:

- Horizontal edges
- Vertical edges
- Corners
- Curves
- Textures
- Shapes

---

# Filters (Kernels)

A filter is a small matrix.

Common sizes:

- 3×3
- 5×5
- 7×7

Each filter learns one feature.

Example:

```
Filter 1 → Edges

Filter 2 → Circles

Filter 3 → Texture

Filter 64 → Eyes

Filter 128 → Faces
```

---

# Feature Maps

Every filter creates one feature map.

```
Input Image

↓

64 Filters

↓

64 Feature Maps
```

More filters:

- Better feature extraction
- Higher computation
- More memory usage

---

# Stride

Stride determines how far the filter moves.

Stride = 1

```
████
████
```

More detail.

Stride = 2

```
█ █
█ █
```

Lower computation but less detail.

---

# Padding

Without padding:

Image size decreases after each convolution.

Padding adds zeros around the image.

```
000000
011110
011110
011110
000000
```

Types:

- Valid
- Same

---

# Activation Function

Most CNNs use **ReLU**.

```
ReLU(x) = max(0, x)
```

Benefits:

- Fast
- Prevents vanishing gradients
- Sparse activation

---

# Pooling Layer

Purpose:

Reduce spatial dimensions.

## Max Pooling

```
1 3
5 2

↓

5
```

Keeps strongest feature.

---

## Average Pooling

```
1 3
5 2

↓

2.75
```

Typical configuration:

- 2×2 Pool Size
- Stride = 2

Benefits:

- Faster computation
- Lower memory usage
- Translation invariance

---

# Batch Normalization

Normalizes activations during training.

Typical order:

```
Conv

↓

BatchNorm

↓

ReLU
```

Benefits:

- Faster convergence
- Stable training
- Allows higher learning rates

---

# Dropout

Randomly disables neurons during training.

```
100 Neurons

↓

Dropout (0.5)

↓

≈50 Active
```

Helps reduce overfitting.

---

# Flatten

Converts feature maps into a vector.

```
32 × 32 × 64

↓

65,536 Features
```

Feeds Dense layers.

---

# Dense Layer

Traditional fully connected neural network.

Purpose:

- Combine extracted features
- Produce final prediction

---

# Output Layer

Classification

```
Softmax
```

Binary Classification

```
Sigmoid
```

Regression

```
Linear
```

---

# Typical CNN Hyperparameters

| Hyperparameter | Typical Value |
|----------------|---------------|
| Kernel Size | 3×3 |
| Stride | 1 |
| Padding | Same |
| Filters | 32 → 64 → 128 → 256 |
| Pool Size | 2×2 |
| Activation | ReLU |
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Batch Size | 32–128 |
| Epochs | 10–100 |

---

# Popular CNN Architectures

| Architecture | Contribution |
|--------------|--------------|
| LeNet | First successful CNN |
| AlexNet | Started modern deep learning revolution |
| VGG16 | Simple and deep architecture |
| GoogLeNet | Inception modules |
| ResNet | Residual learning |
| DenseNet | Dense feature reuse |
| MobileNet | Mobile-friendly CNN |
| EfficientNet | Efficient model scaling |

---

# Advantages

- Excellent image recognition
- Automatic feature extraction
- Parameter sharing
- Translation invariant
- Highly accurate

---

# Limitations

- Requires large datasets
- Computationally expensive
- Less interpretable
- Mainly suited for spatial data

---

# When Should I Use CNN?

| Data Type | CNN Suitable? |
|------------|---------------|
| Images | ✅ Excellent |
| Medical Images | ✅ |
| Satellite Images | ✅ |
| Video Frames | ✅ |
| OCR | ✅ |
| Audio Spectrograms | ✅ |
| Time Series (1D CNN) | ✅ Sometimes |
| Tabular Data | ❌ Usually No |
| Text | ⚠️ Occasionally |

---

# CNN vs ANN

| ANN | CNN |
|------|------|
| Fully Connected | Local Connections |
| Large Parameter Count | Parameter Sharing |
| Ignores Spatial Structure | Preserves Spatial Structure |
| General Purpose | Vision Specialized |

---

# CNN Training Pipeline

```
Images

↓

Data Augmentation

↓

CNN

↓

Loss Function

↓

Backpropagation

↓

Optimizer

↓

Updated Filters

↓

Repeat
```

---

# Practical Design Tips

- Prefer **3×3 kernels**
- Increase filters gradually (32 → 64 → 128 → 256)
- Use Batch Normalization
- Use Max Pooling
- Apply Dropout before Dense layers
- Prefer Global Average Pooling in modern architectures
- Use Transfer Learning whenever possible

---

# CNN in the Deep Learning Landscape

```
Machine Learning

└── Deep Learning
    ├── ANN
    ├── CNN
    ├── RNN
    ├── LSTM
    ├── GRU
    ├── Transformer
    └── Graph Neural Networks
```

---

# CNN Applications in Opsimind

Although CNN is **not part of Opsimind's core reasoning engine**, it can provide valuable visual intelligence.

| Opsimind Capability | CNN Usage | Priority |
|----------------------|-----------|----------|
| Dashboard Screenshot Analysis | Detect broken widgets and UI anomalies | ⭐⭐⭐⭐ |
| Infrastructure Diagram Understanding | Extract topology from architecture diagrams | ⭐⭐⭐⭐ |
| OCR for Logs and PDFs | Read embedded text before LLM processing | ⭐⭐⭐⭐ |
| Incident Screenshot Analysis | Classify UI errors and dialogs | ⭐⭐⭐ |
| Heatmap Analysis | Detect abnormal visual patterns | ⭐⭐⭐ |
| Data Center Camera Monitoring | Equipment monitoring | ⭐⭐ |
| Handwritten Notes | OCR and digitization | ⭐ |

---

# Future Opsimind Vision

```
Monitoring Data
      │
      ├── Metrics ─────────────► Time-Series Models
      ├── Logs ────────────────► LLM + RAG
      ├── Traces ──────────────► Graph Intelligence
      ├── Topology ────────────► Knowledge Graph
      └── Images
             │
             ▼
            CNN
             │
             ▼
     Visual Feature Extraction
             │
             ▼
      Multimodal Reasoning
             │
             ▼
     Opsimind Decision Engine
```

---

# Key Takeaways

✅ CNN is specialized for image and spatial data.

✅ Convolution extracts local features.

✅ Pooling reduces computation.

✅ CNN automatically learns visual patterns.

✅ Modern CNNs often use BatchNorm, Dropout, and Transfer Learning.

✅ CNN is an enabling technology for visual intelligence in Opsimind, especially for screenshot analysis, OCR, and infrastructure diagram understanding.

---

> **Rule of Thumb**
>
> Use **CNN** whenever your data has **spatial structure** (images, videos, spectrograms, or diagrams). For text, sequential data, and reasoning tasks, modern architectures such as **Transformers** are generally a better choice.