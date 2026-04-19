# End-to-End fMRI Reliability and Reproducibility Pipeline

An advanced capstone project implementing a complete task-fMRI workflow with emphasis on methodological rigour, reproducibility, and statistical inference. Using an open task-fMRI sample dataset from Nilearn, this repository evaluates how preprocessing choices and thresholding strategies influence activation results.

This repository serves as the capstone methods project within the Neuroimaging Methods Lab portfolio.

---

## Overview

Neuroimaging conclusions are shaped not only by the data but also by the analytical decisions made during preprocessing and model estimation. This project was designed to examine those decisions through a transparent end-to-end pipeline.

The workflow moves from data inspection and quality checks to first-level GLM analysis, preprocessing sensitivity testing, statistical threshold comparison, and final interpretation.

---

## Quick Start

```bash id="b2bu2c"
pip install nilearn nibabel pandas numpy matplotlib scikit-learn
```

Start with `notebooks/01_data_loading.ipynb` and progress sequentially through the workflow.

---

## Objectives

* Build a complete task-fMRI analysis pipeline using open data
* Fit a first-level General Linear Model (GLM)
* Generate interpretable task contrasts
* Evaluate sensitivity to spatial smoothing parameters
* Compare uncorrected and corrected statistical thresholds
* Demonstrate principles of reproducibility in neuroimaging
* Summarize findings through structured reporting

---

## Dataset

**Source:** Nilearn task-fMRI sample dataset (`fetch_localizer_first_level()`)

### Dataset Characteristics

* 4D functional MRI image
* Shape: **53 × 63 × 46 × 128**
* 128 time volumes
* 80 task events
* 10 experimental conditions

### Example Conditions

* sentence_reading
* sentence_listening
* audio_computation
* visual_computation
* checkerboard stimulation
* left/right-hand button-press tasks

---

## Repository Structure

```text id="swl9e1"
repo6-fmri-reproducibility-pipeline/
├── notebooks/
│   ├── 01_data_loading.ipynb
│   ├── 02_first_level_glm.ipynb
│   ├── 03_preprocessing_sensitivity.ipynb
│   ├── 04_thresholding_and_inference.ipynb
│   └── 05_final_report_and_interpretation.ipynb
│
├── figures/
│   ├── Design matrix.png
│   ├── FDR Corrected.png
│   ├── Mean functional image.png
│   ├── More Conservative Threshold.png
│   ├── Uncorrected Threshold.png
│   ├── reading listening activation map.png
│   ├── smoothing_0mm.png
│   ├── smoothing_5mm.png
│   └── smoothing_8mm.png
│
├── README.md
├── LICENSE
└── .gitignore
```

---

## Analysis Workflow

## 1. Data Loading and Quality Checks

* Loaded functional image and events metadata
* Verified image dimensions and task conditions
* Generated mean functional image for visual inspection

## 2. First-Level GLM Analysis

* Modelled task regressors using canonical HRF
* Included drift regressors and an intercept term
* Computed contrast:

**sentence_reading − sentence_listening**

## 3. Preprocessing Sensitivity Analysis

Compared activation results across smoothing levels:

* 0 mm
* 5 mm
* 8 mm

## 4. Statistical Inference Comparison

Compared activation maps using:

* Uncorrected threshold (`z > 3.0`)
* FDR correction (`q < 0.05`)
* Conservative threshold (`z > 4.0`)

## 5. Final Interpretation Report

Summarized findings, limitations, and future directions.

---

## Key Results

## Effect of Spatial Smoothing

Increasing smoothing reduced peak z-scores while expanding the spatial extent of clusters.

| Smoothing | Peak z-score |
| --------- | ------------ |
| 0 mm      | 6.44         |
| 5 mm      | 5.98         |
| 8 mm      | 5.25         |

## Effect of Thresholding

Statistical conclusions changed depending on the inferential strategy.

* Liberal thresholds retained more voxels
* FDR improved control of false discoveries
* Conservative thresholds increased specificity

**FDR-derived threshold:** 3.289

---

## Selected Outputs

* Design matrix visualization
* Sentence reading vs listening activation contrast
* Smoothing comparison maps
* Thresholding and FDR comparison maps

---

## Why This Project Matters

Reliable neuroimaging findings depend on informed analytical decisions. By explicitly comparing preprocessing and thresholding choices, this project highlights why reproducible neuroscience requires both technical execution and critical statistical reasoning.

---

## Limitations

* Single-subject sample limits population-level generalization
* The public demonstration dataset is modest in scale
* Only selected preprocessing parameters were varied
* No external replication dataset was included

---

## Future Directions

* Extend to multi-subject group-level datasets
* Compare additional preprocessing pipelines
* Add motion and confound regression analyses
* Evaluate cross-dataset reproducibility
* Explore prediction from activation patterns

---

## Tools Used

* Python
* Nilearn
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook
* Google Colab

---

## Maintained By

**Aditya Sundaray**
