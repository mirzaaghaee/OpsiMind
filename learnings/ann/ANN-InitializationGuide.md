# 🏗️ ANN Weight Initialization Cheat Sheet

> **Purpose:** A practical reference for selecting the appropriate weight initialization technique when designing Artificial Neural Networks (ANNs).

---

# 📌 Quick Decision Guide

| If you're using... | Recommended Initialization |
|--------------------|----------------------------|
| ReLU | He (Kaiming) Initialization |
| Leaky ReLU | He (Kaiming) Initialization |
| ELU | He Initialization |
| GELU | He Initialization |
| Swish | He Initialization |
| Mish | He Initialization |
| Sigmoid | Xavier (Glorot) Initialization |
| Tanh | Xavier (Glorot) Initialization |
| SELU | LeCun Initialization |
| RNN | Xavier Initialization |
| LSTM | Xavier + Orthogonal |
| GRU | Xavier + Orthogonal |
| Transformer | Xavier / Normal Initialization |
| CNN | He Initialization |

---

# 📊 Initialization Method Comparison

| Initialization | Best Activation | Keeps Variance Stable | Typical Use |
|----------------|-----------------|-----------------------|-------------|
| **Zeros** | ❌ None | ❌ No | Never for weights |
| **Ones** | ❌ None | ❌ No | Rare (bias only) |
| **Random Uniform** | Any | ❌ No | Educational examples |
| **Random Normal** | Any | ❌ No | Simple experiments |
| **Xavier Uniform** | Sigmoid / Tanh | ✅ Yes | Classical Neural Networks |
| **Xavier Normal** | Sigmoid / Tanh | ✅ Yes | Deep Networks |
| **He Uniform** | ReLU Family | ✅ Yes | Modern Deep Learning |
| **He Normal** | ReLU Family | ✅ Yes | CNNs |
| **LeCun Uniform** | SELU | ✅ Yes | Self-Normalizing Networks |
| **LeCun Normal** | SELU | ✅ Yes | Deep SELU Networks |
| **Orthogonal** | RNN / LSTM | ✅ Yes | Recurrent Networks |

---

# 📖 What Does Each Technique Do?

| Initialization | Main Idea |
|----------------|-----------|
| **Zeros** | All neurons start identically ❌ |
| **Random** | Breaks symmetry but may explode/vanish gradients |
| **Xavier** | Keeps variance constant for Sigmoid/Tanh |
| **He** | Compensates for ReLU neurons becoming inactive |
| **LeCun** | Designed specifically for SELU |
| **Orthogonal** | Preserves information flow across many recurrent steps |

---

# 🎯 Which Initialization Should I Choose?

| Model | Best Choice |
|--------|-------------|
| Feedforward ANN | ✅ He |
| Deep ANN | ✅ He |
| CNN | ✅ He Normal |
| ResNet | ✅ He Normal |
| EfficientNet | ✅ He Normal |
| Transformer | ✅ Xavier |
| BERT | ✅ Xavier |
| GPT | ✅ Xavier |
| Vision Transformer | ✅ Xavier |
| RNN | ✅ Xavier |
| LSTM | ✅ Xavier + Orthogonal |
| GRU | ✅ Xavier + Orthogonal |
| SELU Network | ✅ LeCun |

---

# 🌳 Decision Tree

```text
                    Start
                      │
          Which activation function?
                      │
     ┌────────────┬────────────┬─────────────┐
     │            │            │
   ReLU       Sigmoid/Tanh    SELU
     │            │            │
     ▼            ▼            ▼
 He Init     Xavier Init   LeCun Init
     │
     ▼
  Recurrent?
     │
 ┌───┴────┐
 │        │
No       Yes
 │        │
 ▼        ▼
He     Orthogonal
```

---

# ⚖️ Advantages & Drawbacks

| Initialization | Advantages | Drawbacks |
|----------------|------------|-----------|
| **Random** | Easy | Unstable training |
| **Xavier** | Prevents vanishing gradients | Not ideal for ReLU |
| **He** | Excellent for ReLU networks | Not designed for Sigmoid |
| **LeCun** | Perfect for SELU | Rarely used outside SELU |
| **Orthogonal** | Excellent long-term memory | Mostly useful for RNNs |

---

# 📐 Mathematical Formulas

| Method | Formula |
|---------|---------|
| Xavier Uniform | ±√(6 / (fan_in + fan_out)) |
| Xavier Normal | σ = √(2 / (fan_in + fan_out)) |
| He Uniform | ±√(6 / fan_in) |
| He Normal | σ = √(2 / fan_in) |
| LeCun Normal | σ = √(1 / fan_in) |
| LeCun Uniform | ±√(3 / fan_in) |

> **fan_in** = Number of input connections

> **fan_out** = Number of output connections

---

# 🚀 Modern Best Practices (2026)

### Feedforward Networks

- ✅ He Initialization is the default.
- ✅ Xavier only for Sigmoid/Tanh.

---

### CNNs

- ✅ He Normal is the industry standard.
- ✅ Used in ResNet, DenseNet, MobileNet and many modern CNNs.

---

### Transformers

- ✅ Xavier or small Normal initialization.
- ✅ Combined with Layer Normalization for stability.

---

### Recurrent Networks

- ✅ Orthogonal initialization for recurrent matrices.
- ✅ Xavier for input matrices.

---

### Self-Normalizing Networks

- ✅ Always use LeCun Initialization with SELU.

---

# 🔗 Activation Pairing

| Activation | Recommended Initialization |
|------------|----------------------------|
| Linear | Xavier |
| Sigmoid | Xavier |
| Tanh | Xavier |
| ReLU | He |
| Leaky ReLU | He |
| ELU | He |
| GELU | He |
| Swish | He |
| Mish | He |
| SELU | LeCun |

---

# 🚀 One-Minute Summary

| Activation | Initialization |
|------------|----------------|
| ReLU Family | 🟢 He |
| Sigmoid | 🟢 Xavier |
| Tanh | 🟢 Xavier |
| SELU | 🟢 LeCun |
| LSTM | 🟢 Xavier + Orthogonal |
| Transformer | 🟢 Xavier |

---

# 💡 Rule of Thumb

> **Using ReLU or its variants?**

➡️ **He Initialization**

> **Using Sigmoid or Tanh?**

➡️ **Xavier Initialization**

> **Using SELU?**

➡️ **LeCun Initialization**

> **Training an LSTM or GRU?**

➡️ **Orthogonal + Xavier**

---

# 🧠 Why Weight Initialization Matters

Poor initialization can cause:

- ❌ Vanishing gradients
- ❌ Exploding gradients
- ❌ Very slow convergence
- ❌ Dead ReLU neurons
- ❌ Unstable training

Good initialization helps:

- ✅ Stable forward propagation
- ✅ Stable backpropagation
- ✅ Faster convergence
- ✅ Better accuracy
- ✅ Easier optimization

---

# 🔄 ANN Training Pipeline

```text
                Design ANN
                    │
                    ▼
      Choose Activation Function
                    │
                    ▼
     Initialize Weights Properly
                    │
                    ▼
         Forward Propagation
                    │
                    ▼
          Compute Loss Function
                    │
                    ▼
         Backpropagation
                    │
                    ▼
          Optimizer Updates Weights
                    │
                    ▼
          Repeat Until Convergence
```

---

# 🎓 Remember

Weight initialization determines **where the learning process begins**.

A poor starting point can make learning slow or unstable, while a good initialization allows gradients to flow effectively and helps the optimizer converge faster.

> **Think of it this way:**
>
> - **Activation Function** → *How neurons think*
> - **Weight Initialization** → *Where learning starts*
> - **Loss Function** → *How mistakes are measured*
> - **Optimizer** → *How the network improves*