# CBC Report Classification using Machine Learning

This project aims to classify medical CBC (Complete Blood Count) reports into different result categories using supervised machine learning techniques. It includes data preprocessing, class imbalance handling via synthetic oversampling, and the evaluation of multiple classification models.

---

## Table of Contents

- [Dataset Description](#dataset-description)
- [Preprocessing Steps](#preprocessing-steps)
- [Handling Class Imbalance](#handling-class-imbalance)
- [Model Training](#model-training)
- [Evaluation Metrics](#evaluation-metrics)
- [Results](#results)
- [Requirements](#requirements)
- [Usage](#usage)
- [License](#license)

---

## Dataset Description

The dataset is a collection of anonymized CBC reports stored in CSV format. It contains various hematological parameters along with a `Result` column indicating the diagnostic category. Additional metadata like `Serial` and `Date` were removed as part of preprocessing.

---

## Preprocessing Steps

- Removed non-informative columns: `Serial`, `Date`
- Converted categorical columns (`Gender`, `Result`) into numeric format
- Handled missing values using median imputation for numeric fields
- Applied Min-Max normalization to scale features between 0 and 1

---

## Handling Class Imbalance

To address class imbalance in the dataset:

- Identified minority and majority classes based on label counts
- Applied a custom SMOTE-like oversampling technique using:
  - K-nearest neighbors (k = 5)
  - Linear interpolation between randomly selected minority samples and their neighbors
- Generated synthetic data until class balance was achieved

---

## Model Training

Three classifiers were trained and evaluated:

1. **K-Nearest Neighbors (KNN)**
   - Number of neighbors: 4
   - Distance-based classification

2. **Random Forest (TreeBagger)**
   - 100 trees
   - Out-of-bag prediction enabled

3. **Support Vector Machine (SVM)**
   - Linear kernel
   - Standardized features before training

---

## Evaluation Metrics

Each model was evaluated using:

- **Accuracy**
- **Confusion Matrix**

Train-test split: 80/20 (HoldOut method)

---

## Results

| Model         | Accuracy     |
|---------------|--------------|
| KNN           | ~96.88%      |
| Random Forest | ~96.43%      |
| SVM           | ~97.89%      |

---

## Requirements

- MATLAB (R2020a or later recommended)
- Statistics and Machine Learning Toolbox

---

## Usage

1. Open the script in MATLAB.
2. Ensure the dataset path is correct in the following line:

```matlab
data = readtable("C:\path\to\CBC Report.csv");
