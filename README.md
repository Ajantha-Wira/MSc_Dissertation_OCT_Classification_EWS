# MSc Dissertation — OCT Classification and Early Warning System

**Attention Models for Deep Convolutional Neural Network for Macular Disease Classification:**  
**Development and Evaluation of an Embedding-Based Early Warning Detection System for Clinical Quality Control**

---

**Student:** Ajantha Indunil Wirasinghe (24027813)  
**Supervisor:** Beran Necat  
**Module:** CSC-40098 | Keele University | 2024/26  
**ORCID:** [0009-0009-0785-0597](https://orcid.org/0009-0009-0785-0597)

> This repository contains the Jupyter notebooks and HTML exports for the MSc dissertation.  
> The dissertation has been deposited in the Keele University Research Repository.  
> This codebase forms the foundation for the journal paper:  
> *A Representation-Space Early Warning Framework for Safe Medical AI Screening*  
> (submitted to Computerized Medical Imaging and Graphics, 2026).

---
```
## Repository structure

MSc_Dissertation_OCT_Classification_EWS/
│
├── Model_Training/
│   ├── ResNet_Baseline/       # ResNet-50 — seeds S42, S84, S126, S3407
│   ├── SE_ResNet/             # SE-ResNet50 — seeds S42, S84, S126, S3407
│   ├── CBAM_ResNet/           # CBAM-ResNet50 — seeds S42, S84, S126, S3407
│   ├── Vit_B16/               # ViT-B/16 — seeds S42, S84, S126, S3407
│   └── Master_Evaluation/     # Cross-model evaluation notebook
│
└── Early_Warning_System/
└── Early_Warning_System.ipynb   # EWS implementation notebook
```

Each folder contains `.ipynb` (runnable) and `.html` (static view) files for each seed run.

**Not included in this repository:**
- Model checkpoints (~250 GB) — available on Google Drive (see below)
- Kermany OCT2017 dataset — publicly available (see Dataset section)
- Summative assessments and progress reports — available on Google Drive

---

## Full project on Google Drive

The Google Drive contains the complete project mirror including everything not in this repository:

| Contents | Link |
|----------|------|
| Full project (all notebooks + presentation + progress reports) | [Google Drive](https://drive.google.com/drive/folders/1H9mo2pwBiiApHMl-CnohP172DAZaebU6?usp=sharing) |

Google Drive structure:

```
Project MSc - CSC-40098/
├── 2 - Data/                          # Dataset (not included — see Dataset section)
├── 3 - Experiments/                   # All notebooks (same as this repo)
├── MSc_Dissertation_Early_Warning_System/  # EWS notebook
├── Summative Assessment 2/            # Dissertation document + presentation
├── Summative Assessment 3 - Progress Report/
└── ReadMe.html
```

> Model checkpoints (~250 GB) are not included in Google Drive due to size.  
> Seed values are fixed in all training scripts to maximise reproducibility.

---

## Models trained

| Model | Architecture | Seeds | Best Accuracy |
|-------|-------------|-------|---------------|
| ResNet-50 | Baseline CNN | 42, 84, 126, 3407 | 99.07% |
| SE-ResNet50 | Squeeze-and-Excitation | 42, 84, 126, 3407 | 98.45% |
| CBAM-ResNet50 | Convolutional Block Attention | 42, 84, 126, 3407 | 98.76% |
| ViT-B/16 | Vision Transformer | 42, 84, 126, 3407 | 98.97% |

All models trained on the leakage-corrected Kermany OCT2017 dataset (27,692 duplicates removed before training).

---

## Early Warning System

The EWS notebook (`Early_Warning_System.ipynb`) implements the initial concept developed during this dissertation:

- Uses ResNet-50 embeddings from the penultimate layer (2048-dimensional)
- Applies Mahalanobis distance to detect structurally atypical normal predictions
- Uses cosine alignment to identify directional tendency toward disease classes
- This is the original contribution of this dissertation — no directly comparable prior work integrating an EWS with AI-based retinal image classification was identified in the literature review

This notebook is the direct precursor to the full three-layer EWS framework developed in the subsequent journal paper.

---

## Dataset

The Kermany OCT2017 dataset is publicly available at:  
[https://data.mendeley.com/datasets/rscbjbr9sj/3](https://data.mendeley.com/datasets/rscbjbr9sj/3)

**Important:** Before training, 27,692 duplicate images were removed to correct a data leakage condition documented by Tampu et al. (2022). All reported results use the leakage-corrected dataset.

---

## How to reproduce the results

### Step 1 — Get the code

Clone this repository or download from Google Drive.

### Step 2 — Update the ROOT path in each notebook

**Model training notebooks:**
```python
ROOT = Path(r"C:\Users\Ajanth\Documents\Model_Training")
DATASET_ROOT = Path(r"C:\Ajanth\YourName\Documents\OCT2017")
```

**Master Evaluation notebook:**
```python
ROOT = Path(r"C:\Users\Ajanth\Documents\Model_Training")
DATASET_ROOT = Path(r"C:\Users\Ajantha\Documents\OCT2017")
```

**Early Warning System notebook:**
```python
PROJECT_ROOT = Path(r"C:\Users\Ajantha\Documents\Experiments")
```

### Step 3 — Run notebooks in order

Run all four seed notebooks per architecture, then Master Evaluation, then the EWS notebook.

> Exact figures require the saved checkpoints. Retraining from scratch may produce marginally different values due to non-deterministic GPU operations, even with fixed seeds.

---

## Environment

Python 3.x
PyTorch (with CUDA for GPU acceleration)
torchvision
timm (for ViT-B/16)
scikit-learn
numpy, pandas, matplotlib, seaborn, Pillow

---

## Related work

**Journal paper (submitted 2026):**  
Wirasinghe, A.I. (2026) *A Representation-Space Early Warning Framework for Safe Medical AI Screening: Detecting Structurally Atypical Normal Predictions in OCT.* Submitted to Computerized Medical Imaging and Graphics.

**Preprints (earlier separate contributions):**
- Wirasinghe, A.I. (2026) An Embedding-Based Post-Classification Safety Layer. Zenodo. [https://doi.org/10.5281/zenodo.19748474](https://doi.org/10.5281/zenodo.19748474)
- Wirasinghe, A.I. (2026) Distance Metrics for Representation-Space Safety. Zenodo. [https://doi.org/10.5281/zenodo.19775566](https://doi.org/10.5281/zenodo.19775566)

---

## Citation

Wirasinghe, A.I. (2026) Attention Models for Deep Convolutional Neural Network
for Macular Disease Classification: Development and Evaluation of an
Embedding-Based Early Warning Detection System for Clinical Quality Control.
MSc dissertation, Keele University, Staffordshire.

---

## License

MIT License.

---

## Author

**Ajantha Indunil Wirasinghe**  
MSc Computer Science with Artificial Intelligence, Keele University  
[ORCID: 0009-0009-0785-0597](https://orcid.org/0009-0009-0785-0597)  
[github.com/Ajantha-Wira](https://github.com/Ajantha-Wira)



