# 🔬 IDSC 2026 — Glaucoma Detection using Deep Learning
### Mathematics for Hope in Healthcare

[![IDSC 2026](https://img.shields.io/badge/Competition-IDSC%202026-blue)](https://idsc2026.github.io/)
[![Dataset](https://img.shields.io/badge/Dataset-HYGD%20PhysioNet-green)](https://physionet.org/content/hillel-yaffe-glaucoma-dataset/1.0.0/)
[![Python](https://img.shields.io/badge/Python-3.10-yellow)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/Framework-PyTorch-red)](https://pytorch.org/)

---

## 👥 Team

| Name | Institution |
|------|-------------|
| **Muzafar Ishmurotov** (Team Leader) | Universitas Islam Negeri Maulana Malik Ibrahim Malang, Indonesia |
| **Samandar Ishmurotov** | Dushanbe Innovation Institute, Tajikistan |

---

## 📌 Overview

This project was developed for the **International Data Science Challenge 2026 (IDSC 2026)** under the theme **"Mathematics and Hope in Healthcare"**.

We build an automated **Glaucoma (GON) detection pipeline** using retinal fundus images from the **Hillel Yaffe Glaucoma Dataset (HYGD)** — the first publicly available fundus dataset with gold-standard annotations based on comprehensive ophthalmic examinations.

Glaucoma affects **64.3 million people worldwide**, with ~50% of cases undiagnosed until irreversible vision loss occurs. Our model offers a low-cost, scalable screening tool that can bring hope to patients in regions lacking specialist care.

---
## 📓 View Notebook
👉 [Click here to view the notebook](https://nbviewer.org/github/MuzaffarIshmurotov/IDSC2026-Glaucoma-Detection/blob/main/Hillel_Yaffe_Glaucoma_Dataset_(HYGD)_A_Gold_Standard_Annotated_Fundus_Dataset_for_Glaucoma_Detection.ipynb)

## 🎯 Task

**Binary classification:** Given a retinal fundus image, predict whether the patient has:
- `GON+` — Glaucomatous Optic Neuropathy (glaucoma)
- `GON-` — No glaucoma (healthy)

---

## 📦 Dataset

**Hillel Yaffe Glaucoma Dataset (HYGD)** — hosted on PhysioNet

| Property | Value |
|----------|-------|
| Total images | 747 |
| GON+ (glaucoma) | 548 (73.4%) |
| GON- (healthy) | 199 (26.6%) |
| Patients | 288 |
| Format | JPG + Labels.csv |
| Quality scores | Included (1–10) |

> Download from: https://physionet.org/content/hillel-yaffe-glaucoma-dataset/1.0.0/

---

## 🧠 Methodology

- **Model:** EfficientNet-B3 (pretrained on ImageNet, transfer learning)
- **Loss:** Weighted Cross-Entropy (handles 73/27 class imbalance)
- **Augmentation:** Random flips, rotation, color jitter
- **Innovation:** Quality-aware confidence adjustment using FundusQ-Net scores
- **Interpretability:** Grad-CAM saliency maps on the optic disc region
- **Hardware:** NVIDIA T4 GPU (Google Colab)

---

## 📊 Results

| Metric | Value |
|--------|-------|
| Test Accuracy | **93.81%** |
| AUC-ROC | **0.9259** |
| GON+ Recall (Sensitivity) | **95%** |
| GON+ Precision | 96% |
| GON- Recall (Specificity) | 90% |
| Macro F1 | 0.92 |
| Weighted F1 | 0.94 |

---

## 🖼️ Sample Results

### Grad-CAM Interpretability
The model correctly focuses on the **optic disc region** for GON+ predictions — consistent with clinical diagnosis of glaucoma.

### Quality-Aware Prediction
We propose a novel mechanism that scales model confidence by image quality score:

```
adjusted_confidence = raw_confidence × (quality_score / 10)
```

This reduces overconfident predictions on low-quality fundus images.

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/IDSC2026-Glaucoma-Detection.git
cd IDSC2026-Glaucoma-Detection
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
```bash
wget -r -N -c -np https://physionet.org/files/hillel-yaffe-glaucoma-dataset/1.0.0/
```

### 4. Run the notebook
Open `IDSC2026_Glaucoma_Detection.ipynb` in Google Colab or Jupyter Notebook and run all cells.

> ⚡ **Recommended:** Use Google Colab with GPU runtime (Runtime → Change runtime type → T4 GPU)

---

## 📁 Repository Structure

```
IDSC2026-Glaucoma-Detection/
├── IDSC2026_Glaucoma_Detection.ipynb   # Main notebook (full pipeline)
├── requirements.txt                     # Python dependencies
└── README.md                            # This file
```

---

## 📚 Citations

**Dataset:**
> Abramovich, O., Pizem, H., Fhima, J., Berkowitz, E., Gofrit, B., Van Eijgen, J., Blumenthal, E., & Behar, J. (2025). Hillel Yaffe Glaucoma Dataset (HYGD): A Gold-Standard Annotated Fundus Dataset for Glaucoma Detection (version 1.0.0). PhysioNet. https://doi.org/10.13026/z0ak-km33

**PhysioNet Platform:**
> Goldberger, A., Amaral, L., Glass, L., Hausdorff, J., Ivanov, P. C., Mark, R., ... & Stanley, H. E. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals. Circulation [Online]. 101(23), pp. e215–e220.

---

## 📄 License

This project is for academic and competition purposes only. The HYGD dataset is licensed under the Open Data Commons Attribution License v1.0.
