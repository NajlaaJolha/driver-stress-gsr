# GSR-Based Driver Stress Classification

This repository contains the code for detecting driver stress using Galvanic Skin Response (GSR) signals.

## What This Code Does

- Downloads the DriveDB (SRAD) dataset from PhysioNet
- Preprocesses GSR signals (removes noise, extracts features)
- Trains machine learning models (Random Forest, XGBoost, CatBoost, etc.)
- Evaluates models using subject-independent validation (LOSO)

## Key Results

| Task                             | Best Model  | Accuracy | F1-Score |
|----------------------------------|-------------|----------|----------|
| Binary (Rest vs Stress)          | Extra Trees | 84.9%    | 0.830    |
| Multiclass (Rest, Highway, City) | CatBoost    | 66.0%    | 0.608    |

## Requirements

You need Python installed. Then install the required packages:

pip install -r requirements.txt

How to Run
Option A: Google Colab (Recommended)
Upload driver_stress_gsr_pipeline.ipynb to Google Colab

Run the cells in order

Results will be saved to your Google Drive at: /content/drive/MyDrive/GSR_Results/

Option B: Local Jupyter Notebook
Install dependencies:

pip install -r requirements.txt
Run the notebook:

jupyter notebook driver_stress_gsr_pipeline.ipynb
Results will be saved to: ./GSR_Results/

Notebook Structure
Cell	Content
Cells 1-3	Data loading and visualization
Cells 4-7	Feature extraction
Cells 8-17	Classification pipeline

Output
All results are saved to timestamped folders:

GSR_Results/
├── run_YYYYMMDD_HHMMSS/
│   ├── binary/
│   │   ├── summary_LOSO.csv
│   │   ├── confusion_matrix_best_model_binary_stress.png
│   │   └── ...
│   ├── multiclass/
│   │   ├── summary_LOSO.csv
│   │   ├── confusion_matrix_best_model_multiclass.png
│   │   └── ...
│   └── validation_strategy_comparison_full.csv

Citation
If you use this code, please cite the corresponding paper.

Contact
For questions, please open an issue on GitHub: 

