# Heterogeneous GNN for Member–Event Link Prediction 🔗🧠

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-red)
![PyG](https://img.shields.io/badge/PyG-PyTorch%20Geometric-orange)
![Status](https://img.shields.io/badge/Status-Research%2FPrototype-yellow)

A practical pipeline to **build member & event feature vectors**, **generate a heterogeneous graph**, and **train a Heterogeneous GNN (PyTorch Geometric)** for **link prediction** (e.g., *Will a member attend an event?*).

> ⚠️ **Privacy-first repo:** This repository intentionally **does not include any company data**. All examples use **placeholders** and **schemas** only.

---

## ✨ What this repo does

- ✅ Builds **member feature vectors** (optionally with **StandardScaler + PCA**)
- ✅ Builds **event features** (time, duration, location vectors, tags/keywords, etc.)
- ✅ Creates **adjacency lists / edge lists** from member–event interactions
- ✅ Converts intermediate artifacts to **JSON** (portable data exchange)
- ✅ Trains and evaluates a **heterogeneous link-level GNN** using **PyTorch Geometric**

---

## 🧩 Pipeline overview

1. **Preprocess & align entities**
   - Ensure member IDs are consistent across all sources
   - Generate shared “common events” list (stable event index)

2. **Create features**
   - Member vectors (dense numerical vectors)
   - Event vectors (time/date, duration, location embeddings, tags/keywords)

3. **Build graph**
   - Node types: `member`, `event`
   - Edge types: `member -> event` (attendance/interactions)

4. **Train GNN**
   - Edge-level train/val/test split
   - Neighbor sampling loaders
   - Heterogeneous GNN encoder + link predictor head
   - Evaluate using ROC-AUC (and optionally Precision/Recall)

---

## 📁 Repository structure (recommended)

```text
.
├── notebooks/
│   ├── 01_feature_engineering.ipynb        # member/event feature creation, vectors
│   ├── 02_json_generation.ipynb            # export features/edges to json
│   └── 03_hetero_gnn_link_prediction.ipynb # PyG hetero GNN training & evaluation
│
├── src/ (optional if you modularize later)
│   ├── data/
│   ├── features/
│   ├── graph/
│   └── models/
│
├── data/
│   ├── raw/        # (ignored) private company data placed locally
│   └── processed/  # (ignored) generated artifacts (vectors/json/edges)
│
├── .gitignore
├── requirements.txt
└── README.md
