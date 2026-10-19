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
If you use this code, please cite the corresponding paper:

``` bibtex
@Article{Jolha2026,
author={Jolha, Firas
and Jolha, Najlaa
and Al-imam, Wael
and Massoud, Rasha},
title={Evaluating the Performance of a GSR-Based Prediction Model for Driver Stress Detection in Naturalistic Driving},
journal={International Journal of Computational Intelligence Systems},
year={2026},
month={Oct},
day={14},
abstract={Detecting driver stress through physiological monitoring is essential for road safety, as elevated arousal can affect attention and decision-making. This study develops and evaluates a prediction model for distinguishing stress-related driving states using Galvanic Skin Response (GSR) alone from hand and foot sensors under naturalistic driving conditions using the public DriveDB dataset. Rest, Highway, and City serve as proxy stress labels; independent ratings are not available in the public release. Ten recordings from at most nine healthy adult drivers were analyzed through artifact removal, preprocessing, and extraction of statistical, skin conductance response (SCR), and spectral features. Using leave-one-subject-out (LOSO) validation, the Extra Trees classifier achieved the best binary performance in separating Rest from stress-related driving, with 85.0{\%} accuracy (95{\%} CI: 77.4{\%}--92.6{\%}), a Macro-F1 score of 0.839 (95{\%} CI: 0.760--0.918), and an AUC of 0.924 (95{\%} CI: 0.865--0.983). For three-class classification, it achieved 65.6{\%} accuracy and a Cohen's kappa of 0.471. Ablation analysis showed that foot GSR alone provided the highest single-sensor performance, reaching 86.6{\%} accuracy and an F1-score of 0.851, outperforming hand-only measurements and achieving comparable results to combined hand--foot GSR. The feature selection procedure chose the same 20 features in every fold. Reducing the feature set from 34 to 20 statistically selected features caused only a minor F1-score reduction (0.850 to 0.839), supporting efficient implementation. These findings suggest that GSR alone, especially foot-based sensing, can separate resting from stress-related driving states in this small dataset. Because labels reflect driving conditions rather than measured stress, and we did not control for physical activity or workload, larger, independently labeled datasets are needed before practical use.},
issn={1875-6883},
doi={10.1007/s44196-026-01634-z},
url={https://doi.org/10.1007/s44196-026-01634-z}
}
```



## Contact
For questions, please open an issue on GitHub.
