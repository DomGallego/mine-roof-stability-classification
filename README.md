# Mine-Roof-Stability-Classification

[![PypI version](https://img.shields.io/pypi/v/lazypredict.svg)](https://pypi.org/project/lazypredict)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Echoes of Safety: Using Acoustic Data and Machine Learning to Classify Mine Roof Stability**

**Affiliation:** Artificial Intelligence Program, University of the Philippines Diliman
**Date:** June 22, 2024

## Abstract

Accurate mine roof stability assessment is crucial for underground miners' safety. This project aims to develop a machine learning model that can accurately classify mine roof stability from acoustic impact recordings. We explored Discrete Wavelet Transform (DWT) and Power Spectral Density (PSD) for feature extraction from audio datasets, combined with dimensionality reduction techniques like PCA, KernelPCA, and UMAP.  XGBoost and LightGBM classifiers were evaluated, achieving accuracies of 89% and 88% respectively. LightGBM demonstrated significantly faster inference speed, highlighting the importance of speed in real-time applications.

## Introduction

Underground mining is inherently dangerous, and ensuring miner safety is paramount. Mine roof falls are a significant cause of fatalities and injuries in underground mining. Traditional roof stability assessment relies on miners striking the roof with scaling bars and interpreting the sound ("tight" or "drummy"), which is subjective and experience-dependent. This project explores automating mine roof stability assessment using machine learning and acoustic impact data.

## Objectives

This study aims to:
- Develop machine learning classification algorithms for mine roof stability assessment using acoustic data.
- Compare the performance of different machine learning models and feature extraction techniques.
- Achieve high accuracy in classifying mine roof stability ("tight" or "drummy") from impact recordings.
- Evaluate the inference speed of the models for potential real-time deployment.

## Methods

**1. Dataset:** A library of labeled roof impacts from potash mine sites in Saskatchewan was used. The dataset consists of "tight" (stable) and "drummy" (unstable) roof impacts, recorded using acoustic sensors.

**2. Data Preprocessing and Feature Extraction:**
    - **Data Trimming:** Audio recordings were trimmed to the first 8000 data points (approximately 0.16 seconds) to balance accuracy and computational efficiency.
    - **Feature Extraction:** Discrete Wavelet Transform (DWT) and Power Spectral Density (PSD) were used to extract features from the trimmed audio data.
    - **Statistical Features:** Statistical measures (mean, standard deviation, skewness, kurtosis, max, min) were added to the extracted features to enhance the feature set.

**3. Dimensionality Reduction:** Principal Component Analysis (PCA), Kernel PCA (KPCA), and Uniform Manifold Approximation and Projection (UMAP) were employed for dimensionality reduction to improve model performance and manage high-dimensional data.

**4. Model Training and Evaluation:**
    - **Candidate Classifiers:** LazyPredict AutoML library was used to train and evaluate multiple classifiers, including LightGBM, XGBoost, AdaBoost, Random Forest, Bagging, Logistic Regression, Ridge Classifier, Gaussian Naive Bayes, and Quadratic Discriminant Analysis.
    - **Hyperparameter Tuning:** Optuna was used for hyperparameter tuning of the top-performing classifiers and preprocessing steps.
    - **Model Evaluation:** Model performance was evaluated based on accuracy and F1-score using 5-fold cross-validation. Inference speed was also measured for the best models.

## Results

- **Candidate Classifiers (LazyPredict):** LightGBM and XGBoost classifiers showed the highest accuracy in the initial AutoML evaluation using default parameters.
- **Best Models (Hyperparameter Tuning):**
    - **XGBoost with DWT:** Achieved the highest accuracy of 89% and an F1-score of 0.88. Inference speed was 2.19 seconds.
    - **LightGBM with DWT:** Achieved a slightly lower accuracy of 88% and F1-score of 0.88, but with a significantly faster inference speed of 0.15 seconds.
- **Dimensionality Reduction:** Dimensionality reduction techniques, including PCA, KPCA, and UMAP, did not consistently improve model accuracy in this study.

## Conclusion

XGBoost and LightGBM classifiers demonstrated strong performance in classifying mine roof stability using acoustic impact data. LightGBM's significantly faster inference speed makes it a potentially more suitable choice for real-time applications in mining environments where speed is critical. The study highlights the effectiveness of DWT and PSD for feature extraction from acoustic data in this domain.

## Repository Contents

This repository contains the code and resources for the "Mine-Roof-Stability-Classification" project, including:

*    Python notebooks and scripts for data preprocessing, feature extraction, model training, and evaluation.
*   [Dataset](https://www.sciencedirect.com/science/article/pii/S235234092200066X) - Description of the dataset used or sample data files.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.