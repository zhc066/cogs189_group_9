# COGS 189 – EEG Motor Imagery Classification

This repository contains the code and notebook for a COGS 189 final project on EEG-based motor imagery (MI) classification using the BCICIV 2a dataset.

## Contents

- `cogs189.ipynb` – main analysis notebook implementing a full MI classification pipeline:
  - EEG preprocessing in MNE (filtering, epoching, artifact rejection, CAR)
  - Bandpower feature extraction (alpha/beta)
  - LDA and SVM classifiers
  - (Optional) EEGNet deep learning classifier when PyTorch is available

Raw EEG data files (e.g., a folder named `BCICIV_2a_gdf/` containing `A01T.gdf`, `A01E.gdf`, ...) are not tracked in this repository and must be downloaded separately.

---

## Quickstart

1. Create and activate a Python virtual environment (recommended).

2. Install required packages:

```powershell
pip install mne numpy scipy scikit-learn matplotlib seaborn pandas
# Optional (for EEGNet):
pip install torch torchvision torchaudio
```

3. Open `cogs189.ipynb` in Jupyter or VS Code and run cells sequentially.

4. Update `DATASET_ROOT` in the notebook to point to the directory holding the BCICIV_2a GDF files (e.g., `./BCICIV_2a_gdf`).

## What the notebook implements

- Loading per-subject training (T) and evaluation (E) GDF sessions using MNE.
- Preprocessing: bandpass 0.5–40 Hz, Common Average Reference (CAR), epoching (-0.5 to 4.0 s), and simple artifact rejection (±100 µV threshold).
- Feature extraction: alpha (8–13 Hz) and beta (13–30 Hz) bandpower via Welch's method.
- Classical classifiers: LDA and SVM (RBF) trained per-subject on bandpower features.
- Optional EEGNet: a compact CNN implemented in PyTorch for end-to-end training on epochs.

## Usage notes

- The notebook uses a stratified train/test split (default `random_state=42`) on the T (training) session for LDA/SVM experiments.
- EEGNet training requires PyTorch and is more computationally intensive; reduce `n_epochs` for faster runs.
- To export numeric results, uncomment the CSV save line in the LDA/SVM summary cell.

## Running the experiments

- Preprocessing and feature extraction: run the cells under "Preprocessing pipeline" and "Feature and label extraction per subject".
- Classical classifiers (LDA / SVM): run the "Classical classifiers" cell to compute per-subject accuracies and plots.
- EEGNet: ensure `torch` is installed and run the EEGNet cells. Consider limiting `SUBJECTS` or lowering `n_epochs` for quicker experiments.

## Reproducibility and tips

- Set `DATASET_ROOT` correctly in the notebook.
- If you get an import error for `torch`, the notebook will skip EEGNet automatically and still run LDA/SVM.
- If you want, I can generate a `requirements.txt` with pinned versions matching the environment used to develop this notebook.

---

If you'd like, I will commit this README update and push it to `origin/main` now.
