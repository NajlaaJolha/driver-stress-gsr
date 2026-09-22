# GSR-Based Driver Stress-Related State Classification

This repository contains the code for classifying driver stress-related states using Galvanic Skin Response (GSR) signals, accompanying the paper "Evaluating the Performance of a GSR-Based Prediction Model for Driver Stress-Related State Recognition in Naturalistic Driving."

**This version matches the results reported in the published paper.** It corrects several issues found during peer review in an earlier internal version: the recording-identifier field is fully excluded from model inputs, the confusion-matrix figures report balanced accuracy (correctly labeled), skin-conductance-response features are grouped correctly, and the validation-strategy comparison table uses one classifier per row.

## What This Code Does

- Downloads the DriveDB (SRAD) dataset from PhysioNet
- Preprocesses GSR signals (removes noise, extracts features)
- Trains machine learning models (Random Forest, XGBoost, CatBoost, Extra Trees, LightGBM)
- Evaluates models using leave-one-recording-out (LOSO) validation

## Key Results

| Task                             | Best Model  | Accuracy | F1-Score |
|----------------------------------|-------------|----------|----------|
| Binary (Rest vs. Stress-Related) | Extra Trees | 85.0%    | 0.839    |
| Multiclass (Rest, Highway, City) | CatBoost    | 65.6%    | 0.602    |

The dataset contains ten recordings from at most nine drivers. See the paper for full details, including feature-category ablations, sensor-placement comparisons, and validation-strategy comparisons.

## Requirements

You need Python installed. Then install the required packages:

    pip install -r requirements.txt

## How to Run

### Option A: Google Colab (Recommended)
Upload `driver_stress_gsr_pipeline.ipynb` to Google Colab

Run the cells in order

Results will be saved to your Google Drive at: `/content/drive/MyDrive/GSR_Results/`

### Option B: Local Jupyter Notebook
Install dependencies:

    pip install -r requirements.txt

Run the notebook:

    jupyter notebook driver_stress_gsr_pipeline.ipynb

Results will be saved to: `./GSR_Results/`

## Notebook Structure

| Cell | Content |
|---|---|
| Cells 1-3 | Data loading and visualization |
| Cells 4-7 | Feature extraction |
| Cells 8-17 | Classification pipeline |

## Output

Results are saved to `GSR_Results/run_YYYYMMDD_HHMMSS/`

- `binary/` - Binary results
- `multiclass/` - Multiclass results
- `validation_comparison.csv` - Validation comparison

## Citation
If you use this code, please cite the corresponding paper.

## Contact
For questions, please open an issue on GitHub.
