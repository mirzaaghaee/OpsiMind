# ⚙️ ANN Optimizer Cheat Sheet

> **Purpose:** A practical reference for selecting the appropriate optimizer when training Artificial Neural Networks (ANNs).

---

# 📌 Quick Decision Guide

| If you're training... | Recommended Optimizer |
|-----------------------|-----------------------|
| Your first ANN | Adam |
| Most Deep Learning Models | AdamW |
| CNN | SGD + Momentum / AdamW |
| Transformer / LLM | AdamW |
| Fine-tuning Pretrained Models | AdamW |
| Very Large Dataset | SGD + Momentum |
| Small Dataset | Adam |
| Noisy Gradients | RMSprop / Adam |
| RNN / LSTM | RMSprop / Adam |
| Reinforcement Learning | Adam |

---

# 📊 Optimizer Comparison

| Optimizer | Learning Rate | Momentum | Adaptive LR | Speed | Memory | Typical Use |
|------------|---------------|----------|-------------|-------|--------|-------------|
| **SGD** | Fixed | ❌ | ❌ | ⭐⭐ | ⭐⭐⭐ | Simple models |
| **SGD + Momentum** | Fixed | ✅ | ❌ | ⭐⭐⭐ | ⭐⭐⭐ | CNNs, Computer Vision |
| **Nesterov Momentum** | Fixed | ✅ | ❌ | ⭐⭐⭐⭐ | ⭐⭐⭐ | Improved SGD |
| **AdaGrad** | Adaptive | ❌ | ✅ | ⭐⭐ | ⭐⭐ | Sparse data |
| **RMSprop** | Adaptive | ❌ | ✅ | ⭐⭐⭐⭐ | ⭐⭐ | RNN, LSTM |
| **Adam** | Adaptive | ✅ | ✅ | ⭐⭐⭐⭐⭐ | ⭐⭐ | General Deep Learning |
| **AdamW** | Adaptive | ✅ | ✅ | ⭐⭐⭐⭐⭐ | ⭐⭐ | Transformers, LLMs |
| **AdaDelta** | Adaptive | ❌ | ✅ | ⭐⭐⭐ | ⭐⭐ | Less common |
| **Nadam** | Adaptive | ✅ | ✅ | ⭐⭐⭐⭐⭐ | ⭐⭐ | Adam + Nesterov |
| **Lion** | Adaptive | ✅ | ✅ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | Emerging large models |

---

# 📖 What Makes Them Different?

| Optimizer | Main Idea |
|------------|-----------|
| **SGD** | Takes small steps toward the minimum |
| **Momentum** | Adds inertia to reduce oscillation |
| **Nesterov** | Looks ahead before updating |
| **AdaGrad** | Larger updates for rare features |
| **RMSprop** | Keeps learning rate stable |
| **Adam** | Combines Momentum + RMSprop |
| **AdamW** | Adam with better weight decay |
| **Nadam** | Adam with Nesterov acceleration |
| **Lion** | Uses sign-based updates to reduce memory |

---

# 🎯 Which Optimizer Should I Choose?

| Model | Best Choice |
|--------|-------------|
| Simple ANN | ✅ Adam |
| CNN | ✅ SGD + Momentum |
| ResNet | ✅ SGD + Momentum |
| EfficientNet | ✅ RMSprop / AdamW |
| Transformer | ✅ AdamW |
| GPT | ✅ AdamW |
| BERT | ✅ AdamW |
| Vision Transformer | ✅ AdamW |
| LSTM | ✅ RMSprop |
| RNN | ✅ RMSprop |
| Reinforcement Learning | ✅ Adam |

---

# 🌳 Decision Tree

```text
                    Start
                      │
          What are you training?
                      │
      ┌───────────────┼────────────────┐
      │               │                │
     CNN       Transformer/LLM      RNN/LSTM
      │               │                │
      ▼               ▼                ▼
 SGD + Momentum     AdamW         RMSprop
      │
      ▼
 Simple ANN?
      │
   Yes ▼
     Adam
```

---

# ⚖️ Optimizer Characteristics

| Optimizer | Advantages | Drawbacks |
|------------|------------|-----------|
| **SGD** | Simple, low memory, excellent generalization | Slow convergence |
| **Momentum** | Faster than SGD | Learning rate tuning required |
| **Nesterov** | Better convergence | Slightly more complex |
| **AdaGrad** | Great for sparse features | Learning rate decreases too much |
| **RMSprop** | Stable training | Can overfit |
| **Adam** | Fast, reliable, little tuning | May generalize worse than SGD |
| **AdamW** | Excellent generalization | Slightly more computation |
| **Nadam** | Faster convergence | Rarely necessary |
| **Lion** | Lower memory usage | Still relatively new |

---

# ⚙️ Default Hyperparameters

| Optimizer | Default Learning Rate |
|------------|----------------------|
| SGD | 0.01 |
| Momentum | 0.01 |
| RMSprop | 0.001 |
| Adam | 0.001 |
| AdamW | 0.001 |
| Nadam | 0.001 |
| Lion | 0.0001–0.001 |

---

# 🚀 Modern Best Practices (2026)

### General Deep Learning

- ✅ Adam is an excellent default for beginners.
- ✅ AdamW is preferred for most modern architectures.
- ✅ Use a learning rate scheduler for better convergence.

---

### Computer Vision

- ✅ SGD + Momentum remains the standard for many CNNs.
- ✅ AdamW is increasingly common for Vision Transformers.

---

### Natural Language Processing

- ✅ AdamW is the standard optimizer for Transformer-based models.
- ✅ Always pair AdamW with learning rate warm-up and decay.

---

### Large Language Models

- ✅ AdamW is the dominant optimizer.
- ✅ Lion is gaining attention due to reduced memory requirements.

---

# 🚀 One-Minute Summary

| Scenario | Recommended Optimizer |
|----------|-----------------------|
| Beginner | 🟢 Adam |
| General Deep Learning | 🟢 AdamW |
| CNN | 🟢 SGD + Momentum |
| Transformer / LLM | 🟢 AdamW |
| RNN / LSTM | 🟢 RMSprop |
| Sparse Features | 🟢 AdaGrad |

---

# 💡 Rule of Thumb

> **Training a standard ANN?**

➡️ **Adam**

> **Training a CNN?**

➡️ **SGD + Momentum**

> **Training a Transformer or LLM?**

➡️ **AdamW**

> **Training an RNN or LSTM?**

➡️ **RMSprop**

---

# 🧠 Remember

An optimizer answers the question:

> **"How should the network update its weights to reduce the loss as efficiently as possible?"**

The training pipeline is:

```text
Input Data
     │
     ▼
Forward Propagation
     │
     ▼
Activation Functions
     │
     ▼
Prediction
     │
     ▼
Loss Function
     │
     ▼
Backpropagation (Gradients)
     │
     ▼
Optimizer
     │
     ▼
Update Weights
     │
     ▼
Repeat Until Convergence
```