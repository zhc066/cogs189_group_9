# COGS 189 – EEG Motor Imagery Classification

This repository contains the code and notebook for a COGS 189 final project on **EEG-based motor imagery (MI) classification** using public datasets (BCI Competition IV 2a).

## Contents

- `cogs189.ipynb` – main analysis notebook with:
  - EEG preprocessing in MNE (filtering, epoching, artifact rejection, CAR)
  - Bandpower feature extraction (alpha/beta)
  - LDA and SVM classifiers
  - (Optional) EEGNet deep learning classifier when PyTorch is available

Raw EEG data files (e.g., `BCICIV_2a_gdf/`) are **not tracked** in git and should be downloaded separately from the original sources.

