# 🧠 ANN Activation Function Cheat Sheet

> **Purpose:** A practical reference for selecting activation functions when designing Artificial Neural Networks (ANNs).

---

# 📌 Quick Decision Guide

| If you're building... | Hidden Layer | Output Layer |
|-----------------------|--------------|--------------|
| Regression Model | ReLU | Linear |
| Binary Classifier | ReLU | Sigmoid |
| Multi-Class Classifier | ReLU | Softmax |
| Multi-Label Classifier | ReLU | Sigmoid |
| CNN | ReLU | Depends on Task |
| Transformer / LLM | GELU | Depends on Task |

---

# 📊 Activation Function Comparison

| Activation | Shape | Typical Use | Output Range | 👍 Advantages | 👎 Drawbacks |
|------------|-------|-------------|--------------|---------------|--------------|
| **Linear** | `/` | Regression Output | (-∞, +∞) | Simple, unrestricted output | No non-linearity |
| **Sigmoid** | `S` | Binary Classification | (0,1) | Probability output | Vanishing gradients |
| **Tanh** | `S` | RNN/LSTM | (-1,1) | Zero-centered | Vanishing gradients |
| **ReLU** | `└╱` | Hidden Layers (Default) | [0,+∞) | Fast, sparse activations | Dead neurons |
| **Leaky ReLU** | `╱╲` | Hidden Layers | (-∞,+∞) | Solves dead ReLU problem | Small negative leakage |
| **ELU** | `⌒╱` | Deep CNNs | (-α,+∞) | Faster convergence | Slightly slower |
| **SELU** | `⌒╱` | Self-Normalizing Networks | (-λα,+∞) | Automatic normalization | Special initialization required |
| **Softplus** | `⌒╱` | Positive Outputs | (0,+∞) | Smooth ReLU | Slower |
| **Swish** | `~╱` | EfficientNet | (-∞,+∞) | Better gradient flow | More computation |
| **Mish** | `∿╱` | Research Models | (-∞,+∞) | Excellent gradients | Computationally expensive |
| **GELU** | `≈╱` | Transformers / LLMs | (-∞,+∞) | State-of-the-art | Slower than ReLU |
| **Softmax** | `⇑` | Multi-Class Output | (0,1), Σ=1 | Probability distribution | Output depends on all neurons |

---

# 📖 Shape Legend

| Symbol | Meaning |
|---------|---------|
| `/` | Linear |
| `S` | Sigmoid / Tanh |
| `└╱` | ReLU |
| `╱╲` | Leaky ReLU |
| `⌒╱` | ELU / SELU / Softplus |
| `~╱` | Swish |
| `∿╱` | Mish |
| `≈╱` | GELU |
| `⇑` | Softmax |

---

# 🎯 Hidden Layer Recommendations

| Network Type | Recommended Activation |
|--------------|------------------------|
| Feedforward ANN (MLP) | ✅ ReLU |
| Deep ANN | ✅ ReLU / Leaky ReLU |
| CNN | ✅ ReLU |
| Very Deep CNN | ✅ ELU / Swish |
| ResNet | ✅ ReLU |
| EfficientNet | ✅ Swish |
| Transformer | ✅ GELU |
| BERT | ✅ GELU |
| GPT | ✅ GELU |
| Vision Transformer (ViT) | ✅ GELU |
| Autoencoder | ✅ ReLU / Leaky ReLU |

---

# 🎯 Output Layer Recommendations

| Task | Activation |
|------|------------|
| Regression | **Linear** |
| Binary Classification | **Sigmoid** |
| Multi-Class Classification | **Softmax** |
| Multi-Label Classification | **Sigmoid** |
| Positive Output Only | **Softplus / ReLU** |
| Output Between -1 and 1 | **Tanh** |

---

# ⚖️ Activation & Loss Function Pairing

| Output Activation | Typical Loss Function |
|-------------------|----------------------|
| Linear | MSE / MAE / Huber Loss |
| Sigmoid | Binary Cross-Entropy (BCE) |
| Softmax | Categorical Cross-Entropy |
| Sigmoid (Multi-Label) | Binary Cross-Entropy (BCE) |

---

# 🌳 Decision Tree

```text
                    Start
                      │
        Is this a Hidden Layer?
             ┌────────┴────────┐
             │                 │
            Yes               No
             │                 │
   Transformer Model?     Output Layer
      ┌──────┴──────┐           │
      │             │           │
     Yes           No     ┌─────┼─────────────┐
      │             │      │     │             │
    GELU          ReLU  Regression Binary   Multi-Class
                             │        │           │
                          Linear   Sigmoid    Softmax
```

---

# ✅ Modern Best Practices (2026)

### Hidden Layers

- ✅ **ReLU** remains the default choice for most neural networks.
- ✅ **GELU** is preferred for Transformer-based architectures.
- ✅ **Leaky ReLU** is a good alternative when dead neurons appear.
- ✅ **Swish** is common in EfficientNet.
- ❌ Avoid **Sigmoid** and **Tanh** in deep hidden layers unless required by the architecture.

---

### Output Layers

| Task | Recommended Activation |
|------|------------------------|
| Regression | ✅ Linear |
| Binary Classification | ✅ Sigmoid |
| Multi-Class Classification | ✅ Softmax |
| Multi-Label Classification | ✅ Sigmoid |

---

# 🚀 One-Minute Summary

| Component | Best Choice |
|-----------|-------------|
| Hidden Layer (General) | 🟢 ReLU |
| Hidden Layer (Transformer) | 🟢 GELU |
| Binary Classification | 🟢 Sigmoid |
| Multi-Class Classification | 🟢 Softmax |
| Multi-Label Classification | 🟢 Sigmoid |
| Regression | 🟢 Linear |

---

# 💡 Rule of Thumb

> **Hidden Layer**
>
> ➜ **ReLU** *(default)*  
> ➜ **GELU** *(Transformers & LLMs)*

> **Output Layer**
>
> - Binary Classification → **Sigmoid**
> - Multi-Class Classification → **Softmax**
> - Multi-Label Classification → **Sigmoid**
> - Regression → **Linear**

---

> **Remember:** The activation function determines **how a neuron decides to fire**, while the **loss function determines how the network learns from its mistakes**.