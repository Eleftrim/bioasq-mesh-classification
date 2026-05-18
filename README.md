# BioASQ MeSH Multi-Label Classification

**Course Assignment — Natural Language Processing (3rd Assignment)**  
**Author:** Eleftheria Trimpou  
**Supervisor:** Ioannis Refanidis  
**University of Macedonia, 2024–2025**

---

## Overview

Multi-label classification of biomedical articles from the BioASQ 2016b dataset,
automatically assigning MeSH (Medical Subject Headings) terms based solely on 
article title and abstract. Implemented with BioBERT and a Top-K label filtering 
strategy to handle the extreme label space dimensionality.

---

## Dataset

[BioASQ 2016b](http://bioasq.org/) — 200,000 PubMed articles  
- Train: 140,000 · Validation: 30,000 · Test: 30,000  
- Original label space: 23,495 unique MeSH terms → reduced to **Top-2000** (91.5% reduction)

---

## Methodology

- **Model:** BioBERT (`dmis-lab/biobert-v1.1`)
- **Strategy:** Top-K label filtering (K=2000 most frequent MeSH terms)
- **Max sequence length:** 384 tokens
- **Loss function:** BCEWithLogitsLoss (multi-label)
- **Optimizer:** AdamW (lr=3e-5) with linear warmup scheduler
- **Training:** 3 epochs, batch size 14, gradient accumulation steps 2
- **Platform:** Kaggle (GPU 16GB)

---

## Key Results

| Metric | Value |
|--------|-------|
| F1-Micro | 0.3918 |
| F1-Macro | 0.0079 |
| Precision (Micro) | 0.577 |
| Recall (Micro) | 0.296 |
| Best Threshold | 0.20 |
| Training Time | ~270 min |

---

## Repository Structure
├── biosaq-phase1.ipynb              # Data preprocessing pipeline
├── biosaqtrimpoueleftheria.ipynb    # Main training & evaluation notebook
└── report/
└── hw3reporttrimpoueleftheria.pdf

---

## Technologies

`Python` `PyTorch` `HuggingFace Transformers` `BioBERT` `scikit-learn`  
`NumPy` `Pandas` `Matplotlib` `Seaborn` `Kaggle`
