# FC_ElectroChar

# 🧪 NMF-ICA Based EELS Spectrum Decomposition

A modular Jupyter Notebook pipeline for decomposing STEM-EELS spectral datasets using **Non-negative Matrix Factorization (NMF)** and **Independent Component Analysis (ICA)**, followed by component segmentation using **KMeans clustering**. Designed for researchers working with **Hyperspy** and **energy-loss spectroscopy** data.

---

## 📌 Features

- ✅ **Two-stage spectral decomposition** (NMF → ICA)
- ✅ Removes negative signal artifacts for physical interpretability
- ✅ Supports flexible number of components (NMF/ICA)
- ✅ **KMeans segmentation** for mapping dominant material phases
- ✅ Fully compatible with Hyperspy `Signal2D` and `EELSSpectrum`

---

## 🧩 Functional Overview

| Function | Description |
|---------|-------------|
| `remove_negative(signal)` | Removes negative values from spectrum by subtracting the minimum |
| `run_nmf(signal, n_components=4)` | Performs NMF decomposition with Poissonian noise normalization |
| `run_ica(signal, n_components=4)` | Applies ICA (FastICA from scikit-learn) after NMF |
| `segment_by_kmeans(signal, n_clusters)` | Clusters component loadings into binary phase masks |

---

## 🔧 Installation

```bash
pip install hyperspy scikit-learn matplotlib numpy
