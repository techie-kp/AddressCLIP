# 📍 AddressCLIP: Image Address Localization using Vision-Language Models

## 🚀 Overview

This project focuses on **Image Address Localization (IAL)** — predicting a **human-readable address** (street + sub-street level) directly from an input image using vision-language models.

The work is based on the paper:

> **AddressCLIP: Empowering Vision-Language Models for City-Wide Image Address Localization**  
> *(arXiv:2407.08156)*

We extend the original framework with **custom improvements and architectural novelties**, achieving significant performance gains.

---

## 🎯 Key Contributions

- ✅ Implemented full **AddressCLIP pipeline** using CLIP (ViT-B/16)
- ✅ Improved performance from **~27% → ~75% SSA-1**
- ✅ Designed and executed **comprehensive ablation study**
- ✅ Added **caption-based semantic supervision**
- ✅ Integrated **geography-aware loss for spatial consistency**
- ✅ Proposed and experimented with **novel architectural extensions**
- ✅ Built full **training, evaluation, and visualization pipeline**

---

## 🧠 Problem Statement

Given an input image:

📷 → 🧠 Model → 📍 Address (Street + Sub-street)

Unlike traditional geo-localization (which predicts coordinates), this project predicts **interpretable textual addresses**.

---

## 🏗️ Architecture

The model consists of:

- 🔹 CLIP Image Encoder
- 🔹 CLIP Text Encoder
- 🔹 Projection Heads:
  - Image Head
  - Address Head
  - Caption Head

### Multi-Loss Training:

- 🧾 **Address Loss (InfoNCE)**
- 📝 **Caption Loss (InfoNCE)**
- 🌍 **Geography Loss (Spatial consistency)**

---

## 📊 Results

### 🔥 Performance Improvement

| Model Version | SSA-1 | SA-1 |
|--------------|------|------|
| Phase-1 (Baseline) | ~27% | ~30% |
| Phase-2 (AddressCLIP) | ~75% | ~78% |
| With Novelty | **~76%** | **~79%** |

---

## 🧪 Ablation Study

We conducted a 5-configuration ablation study:

| Configuration | SSA-1 |
|--------------|------|
| Address only | 76.64% |
| Caption only | 68.27% |
| Address + Caption | 79.12% |
| Address + Geography | 78.97% |
| Full Model | **79.13%** |

### Key Insight:
- Address supervision is primary driver
- Caption + geography provide **complementary gains**

---

## 📈 Training Analysis

- Best checkpoint: **Epoch 52**
- Stable convergence observed with multi-loss training
- SSA-1 used as primary evaluation metric

---

## 🔍 Qualitative Results

### ✅ Correct Predictions
- Accurate street-level localization
- Strong semantic understanding

### ❌ Failure Cases
- Visually similar streets
- Dense urban intersections
- Lack of distinctive landmarks

---

## 🛠️ Tech Stack

- Python 3.10
- PyTorch 2.x
- HuggingFace Transformers
- OpenAI CLIP (ViT-B/16)
- NumPy, Pandas
- Matplotlib

---

## 📁 Project Structure
AddressCLIP/
│
├── major_project_copy.ipynb # Phase-1 (baseline)
├── major_project_copy_2.ipynb # Phase-2 (improved)
├── novelty_transfer.ipynb # Proposed improvements
├── ablation_study_CORRECTED.ipynb # Ablation experiments
│
├── optimized_dataset.py # Dataset handling
├── images/ # Figures and results
│
├── README.md
└── .gitignore


---

## ⚙️ How to Run

### 1. Clone repository
```bash
git clone git@github.com:techie-kp/AddressCLIP.git
cd AddressCLIP
2. Install dependencies
pip install torch torchvision transformers numpy pandas matplotlib
3. Run notebooks
Phase-1:
major_project_copy.ipynb
Phase-2:
major_project_copy_2.ipynb
Novelty:
novelty_transfer.ipynb

📌 Future Work
🚀 Improve sub-street localization accuracy
🧠 Introduce attention-based fusion
🌍 Extend to multi-city datasets
⚡ Optimize inference speed

👨‍💻 Author

Khush Patel
B.Tech — Computational and Data Science
NITK Surathkal

📚 References
Radford et al., CLIP, ICML 2021
Xu et al., AddressCLIP, 2024
Hays & Efros, IM2GPS, CVPR 2008