# 🔬 ML-assisted STEM-EELS Mapping of Catalyst–Ionomer–Carbon Interface in PEMFC Cathodes

## 📝 Associated Publication

This repository accompanies the following research article:

### 📄 **Efficient Probing of Structural Degradation of Catalyst–Ionomer–Carbon Composite Electrode Using Machine Learning-empowered Spectroscopic Imaging**

**Authors:**  
Daehee Yang#, Young-Hoon Kim#, Hyo June Lee#, Sang-Hyeok Yang, Min Hyoung Jung,  
Eun-Byeol Park, Hang Sik Kim, Yerin Jeon, Yuseong Heo, Ka Hyun Kim, Sungyong Cho,  
Yun Sik Kang, Ki Kang Kim, Hangil Lee, Sung-Dae Yim, Jae Hyuck Jang\*,  
Sungchul Lee\*, Young-Min Kim\*

**Journal:**   
**DOI:** 

---

## 🧭 Overview

This repository provides a complete machine-learning-assisted pipeline for analyzing **PEMFC cathode degradation** using **bonding-sensitive STEM-EELS** and **HAADF imaging**. The pipeline segments chemically distinct regions (ionomer, carbon), detects and quantifies catalyst particles, and computes degradation metrics including:

- **Ionomer coverage (IC)**
- **Catalyst contact ratio (CR)**
- **Pt particle area (DI/DA)** in μm²

---

## 📁 Repository Structure

```
.
├── core/                                  # U-Net architecture (Attention U-Net) and post-processing utils
│   └── attention_unet.py
├── model/                                 # Pre-trained Attention U-Net model (not provided)
│   └── [NOT INCLUDED due to license]
├── 1.Ionomer-support_segmentation.ipynb   # C K-edge EELS spectral decomposition (NMF + ICA + clustering)
├── 2.Pt_segmentation.ipynb                # Catalyst segmentation with U-Net, area-based classification
├── 3.Pt_size_analysis.ipynb               # Area histogram and lifecycle comparison
├── 4.Statistical_analysis.ipynb           # Pt-ionomer/carbon/contact quantification
└── README.md
```

> ⚠️ **Note:** The trained model weights are not included due to data policy restrictions.

---

## ⚙️ Pipeline Description

### `1.Ionomer-support_segmentation.ipynb`
- Loads **C K-edge EELS SI** (280–300 eV range)
- Applies **NMF + ICA** for spectral decomposition
- Uses **K-means clustering** to segment:
  - Ionomer-rich (C2 peak ~289 eV)
  - Carbon support (C1/C3)
- Outputs binary masks (ionomer, support)

---

### `2.Pt_segmentation.ipynb`
- Loads HAADF images
- Applies trained **Attention U-Net**
- Detects:
  - **Single Pt particles**
  - **Agglomerated Pt clusters**
- Saves particle area in:
  - `*_single_area.csv`
  - `*_agg_area.csv`

---

### `3.Pt_size_analysis.ipynb`
- Aggregates area distributions across BOL, SOL, EOL stages
- Computes and visualizes:
  - Average particle area
  - Histogram comparison
- Outputs `.csv` summaries

---

### `4.Statistical_analysis.ipynb`
- Combines EELS and HAADF masks
- Computes:
  - **Ionomer Coverage (IC)**: Pt–ionomer overlap
  - **Catalyst Contact Ratio (CR)**: Pt–both-phase overlap
- Outputs:
  - Interface RGB maps
  - `.csv` statistical data

---

## 📦 Requirements

```bash
pip install hyperspy=1.7.3 scikit-learn matplotlib numpy tqdm torch torchvision opencv-python
```

---

## 📖 Citation

If you use this code or data, please cite:

D. Yang#, Y.-H. Kim#, H. J. Lee#, S.-H. Yang, M. H. Jung, E.-B. Park, H. S. Kim, Y. Jeon, Y. Heo, K. H. Kim, S. Cho, Y. S. Kang, K. K. Kim, H. Lee, S.-D. Yim, J. H. Jang*, S. Lee*, Y.-M. Kim*

"Efficient Probing of Structural Degradation of Catalyst–Ionomer–Carbon Composite Electrode Using Machine Learning-empowered Spectroscopic Imaging",  


---

## 📜 License

This project is licensed under the **MIT License**.
