# 🏛️ ANN Architecture Design Cheat Sheet

> **Purpose:** A practical guide for designing Artificial Neural Network (ANN) architectures based on the problem, dataset, and model performance.

---

# 🎯 ANN Design Workflow

```text
Understand the Problem
          │
          ▼
Identify Data Type
          │
          ▼
Choose Architecture
          │
          ▼
Estimate Model Size
          │
          ▼
Design Hidden Layers
          │
          ▼
Choose Activation Functions
          │
          ▼
Choose Weight Initialization
          │
          ▼
Choose Loss Function
          │
          ▼
Choose Optimizer
          │
          ▼
Train & Evaluate
          │
          ▼
Improve Architecture
```

---

# 📌 Step 1 — Identify the Data Type

| Data Type | Recommended Architecture |
|------------|--------------------------|
| Tabular Data | ✅ ANN (MLP) |
| Images | ✅ CNN |
| Time Series | ✅ LSTM / GRU / Transformer |
| Text | ✅ Transformer |
| Audio | ✅ CNN + Transformer |
| Video | ✅ CNN + Transformer |
| Graph Data | ✅ Graph Neural Network (GNN) |

> **Rule:** Never use a larger ANN when a more suitable architecture exists.

---

# 📌 Step 2 — Estimate Problem Complexity

| Problem Complexity | Example | Recommended Depth |
|--------------------|---------|-------------------|
| Very Simple | House Price | 1 Hidden Layer |
| Simple | Customer Segmentation | 1–2 Hidden Layers |
| Medium | Customer Churn | 2–3 Hidden Layers |
| Complex | Fraud Detection | 3–5 Hidden Layers |
| Very Complex | Medical Diagnosis | 4–8 Hidden Layers |

---

# 📌 Step 3 — Consider Dataset Size

| Training Samples | Suggested Model Size |
|------------------|----------------------|
| < 1,000 | Very Small |
| 1K – 10K | Small |
| 10K – 100K | Medium |
| 100K – 1M | Large |
| > 1M | Deep Models Possible |

### Rule

Small datasets → Small models

Large datasets → Larger models

---

# 📌 Step 4 — Number of Input Features

| Number of Features | Suggested Width |
|--------------------|-----------------|
| < 20 | 16–32 neurons |
| 20–100 | 32–64 neurons |
| 100–500 | 64–128 neurons |
| 500–2000 | 128–256 neurons |
| > 2000 | 256–512 neurons |

---

# 📌 Step 5 — Select Hidden Layers

## Very Small ANN

```text
Input
   │
  16
   │
Output
```

---

## Small ANN

```text
Input
   │
  32
   │
  16
   │
Output
```

---

## Medium ANN

```text
Input
   │
 128
   │
  64
   │
  32
   │
Output
```

---

## Large ANN

```text
Input
   │
 256
   │
 128
   │
  64
   │
  32
   │
Output
```

---

# 📌 Step 6 — Follow the Pyramid Rule

✅ Recommended

```text
256
 │
128
 │
64
 │
32
 │
Output
```

❌ Avoid

```text
32
 │
512
 │
16
 │
800
 │
Output
```

A gradual reduction in layer size encourages the network to compress information into more abstract representations.

---

# 📊 Hidden Layer Recommendations

| Problem | Hidden Layers |
|----------|---------------|
| Linear Regression | 0 |
| Simple Regression | 1 |
| Binary Classification | 1–2 |
| Multi-Class Classification | 2–3 |
| Complex Tabular Data | 3–5 |
| Deep Feature Learning | 5–8 |

---

# 📊 Typical Layer Widths

| Network Size | Neurons |
|--------------|----------|
| Tiny | 8 |
| Small | 16 |
| Medium | 32 |
| Standard | 64 |
| Large | 128 |
| Very Large | 256 |
| Huge | 512 |

---

# 📌 Step 7 — Match the Activation Function

| Layer | Recommended Activation |
|--------|------------------------|
| Hidden Layers | ReLU |
| Hidden Layers (Transformer) | GELU |
| Regression Output | Linear |
| Binary Classification | Sigmoid |
| Multi-Class Classification | Softmax |

---

# 📌 Step 8 — Match Weight Initialization

| Activation | Initialization |
|------------|----------------|
| ReLU Family | He |
| Sigmoid | Xavier |
| Tanh | Xavier |
| SELU | LeCun |

---

# 📌 Step 9 — Match the Loss Function

| Task | Loss |
|------|------|
| Regression | MSE |
| Regression + Outliers | Huber |
| Binary Classification | BCE |
| Multi-Class Classification | Categorical Cross-Entropy |
| Multi-Label Classification | BCE |

---

# 📌 Step 10 — Select an Optimizer

| Model | Optimizer |
|--------|-----------|
| General ANN | Adam |
| CNN | SGD + Momentum |
| Transformer | AdamW |
| RNN | RMSprop |

---

# 🌳 ANN Design Decision Tree

```text
                         Start
                           │
                What type of data?
                           │
     ┌──────────────┬───────────────┬──────────────┐
     │              │               │
   Tabular       Image          Sequence/Text
     │              │               │
    ANN           CNN      LSTM / Transformer
     │
     ▼
Estimate Complexity
     │
     ▼
Estimate Dataset Size
     │
     ▼
Choose Hidden Layers
     │
     ▼
Choose Layer Width
     │
     ▼
Choose Activation
     │
     ▼
Choose Initialization
     │
     ▼
Choose Loss
     │
     ▼
Choose Optimizer
     │
     ▼
Train
```

---

# 📈 Diagnosing the Model

## Underfitting

Symptoms

- Low training accuracy
- Low validation accuracy

Solution

- Add neurons
- Add hidden layers
- Train longer
- Improve features

---

## Overfitting

Symptoms

- High training accuracy
- Low validation accuracy

Solution

- Reduce layers
- Reduce neurons
- Add Dropout
- Add L2 Regularization
- Early Stopping
- More training data

---

# 🚀 Model Scaling Strategy

Never start with the largest model.

```text
Small Model
      │
      ▼
Evaluate
      │
      ▼
Still Underfitting?
      │
  Yes ▼ No
Increase Capacity
      │
      ▼
Retrain
```

---

# 💡 Rules of Thumb

✅ Start with the simplest architecture that can solve the problem.

✅ Increase complexity only when necessary.

✅ More layers are not always better.

✅ More neurons are not always better.

✅ Bigger models require more data.

✅ Choose the architecture based on the data type before tuning hyperparameters.

---

# 🚀 One-Minute Summary

| Design Decision | Recommendation |
|-----------------|----------------|
| Data Type | Choose the appropriate architecture (ANN, CNN, Transformer, etc.) |
| Hidden Layers | Start with 1–3 |
| Neurons | 32–128 is a good starting range |
| Layer Shape | Follow the Pyramid Rule |
| Activation | ReLU (hidden), task-specific output activation |
| Initialization | Match to activation (He/Xavier/LeCun) |
| Loss | Match to prediction task |
| Optimizer | Adam (general), AdamW (Transformers), SGD+Momentum (CNNs) |
| Scaling | Increase complexity only if the model underfits |

---

# 🧠 Golden Principle

> **The best ANN is not the biggest ANN.**

A well-designed neural network balances:

- ✔️ Model complexity
- ✔️ Dataset size
- ✔️ Problem difficulty
- ✔️ Generalization ability

The goal is to build **the simplest model that solves the problem reliably**, not the most complex one.