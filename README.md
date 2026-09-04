
# Deep Temporal Models with Attention and Skip Connections

A PyTorch implementation demonstrating how to enhance sequential/time-series deep learning models by integrating **attention mechanisms** and **residual skip connections**.

---

## 📌 What This Notebook Does

* **Data Preparation:** Windows multivariate time-series data using sliding windows for sequential forecasting.
* **Hybrid Architecture:** Implements a deep temporal model (LSTM/GRU/TCN) enhanced with:
  * **Attention:** Dynamically weights important past time steps to capture long-range temporal dependencies.
  * **Skip Connections:** Preserves low-level sequence features and ensures stable gradient flow across layers.
* **Training & Evaluation:** Trains the model using standard regression metrics (MSE/MAE), visualizes train/validation loss convergence, and plots predicted forecasts against ground-truth signals.

---

## 🚀 Quickstart

1. Clone the repo:
   ```bash
   git clone [https://github.com/IshaPatro/DeepTemporalModelsWithAttentionAndSkipConnections.git](https://github.com/IshaPatro/DeepTemporalModelsWithAttentionAndSkipConnections.git)
   cd DeepTemporalModelsWithAttentionAndSkipConnections```

2. Install dependencies:
```bash
pip install torch numpy pandas matplotlib scikit-learn jupyter```


3. Run:
```bash
jupyter notebook DeepTemporalModelsWithAttentionAndSkipConnection.ipynb```



