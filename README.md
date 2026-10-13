# Predictive Maintenance & Machine Failure Prediction

## Project Overview
A machine learning project that predicts machine failures using operational data such as air temperature, process temperature, rotational speed, torque, and tool wear.

The project compares Logistic Regression and Random Forest models and evaluates threshold tuning to improve failure detection in an imbalanced dataset.

## Dataset
- **Name:** AI4I 2020 Predictive Maintenance Dataset
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)
- **Records:** 10,000
- **Original columns:** 14
- **Target:** `Machine failure`

The dataset contains machine type, air temperature, process temperature, rotational speed, torque, tool wear, and machine failure information.

**Note:** This is a simulated dataset. The results demonstrate a machine-learning workflow and do not establish real-world industrial performance.

## Tech Stack
- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Joblib
- Jupyter Notebook

## Project Workflow
1. Load and inspect the dataset.
2. Perform exploratory data analysis (EDA).
3. Analyze class imbalance and feature distributions.
4. Select relevant features and exclude potential data leakage columns.
5. Split data into training and testing sets using stratification.
6. Build preprocessing and classification pipelines.
7. Train and evaluate Logistic Regression and Random Forest.
8. Tune the classification threshold using a validation set.
9. Evaluate the selected threshold on the untouched test set.
10. Analyze feature importance and save the trained model.

## Models and Results

### Logistic Regression
- Accuracy: 82.45%
- Failure-class precision: 14.18%
- Failure-class recall: 82.35%
- Failure-class F1-score: 24.19%

### Random Forest — Default Threshold
- Accuracy: Approximately 98%
- Failure-class precision: 70%
- Failure-class recall: 66%
- Failure-class F1-score: 68%
- Average precision: 0.7575

### Random Forest — Tuned Threshold
The threshold was selected using a validation set to maximize precision while maintaining validation recall of at least 80%.

- Selected threshold: 0.2567
- Test failure-class precision: 46%
- Test failure-class recall: 85%
- Test failure-class F1-score: 59%
- Test accuracy: Approximately 96%
- Test average precision: 0.7575

The tuned threshold improves failure detection but increases false alarms. Average precision remains unchanged because threshold tuning changes the predicted class labels, not the underlying probability scores.

*Metrics are rounded. Confirm that the values match the final notebook outputs before publishing.*

## Feature Importance

The Random Forest model identified these features as the most important:

| Feature | Importance |
|---|---:|
| Torque | 30.72% |
| Rotational speed | 29.64% |
| Tool wear | 20.78% |
| Air temperature | 10.18% |
| Process temperature | 6.90% |

Feature importance reflects the model's relative use of features; it does not establish causation.

## Preventing Data Leakage
The model uses machine type and five operational measurements as input features. Identifier columns and failure-mode columns (`TWF`, `HDF`, `PWF`, `OSF`, and `RNF`) are excluded from the predictors to reduce leakage risk.

## How to Run

### 1. Clone the repository
```bash
git clone https://github.com/SundheepVayyavuru/Predictive-Maintenance-and-Failure-Detection.git
cd Predictive-Maintenance-and-Failure-Detection
```

### 2. Create a virtual environment
```bash
python -m venv .venv
```

### 3. Activate it in Windows PowerShell
```powershell
.\.venv\Scripts\Activate.ps1
```

### 4. Install dependencies
```bash
python -m pip install -r requirements.txt
```

### 5. Download the dataset
Download the AI4I 2020 dataset from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset) and place the CSV file at:

`data/ai4i2020.csv`

### 6. Launch Jupyter Notebook
Run this command from the project root:

```bash
jupyter notebook
```

Open `notebooks/01_data_exploration.ipynb` and run the notebook cells.

The notebook uses relative paths, so launching Jupyter from the project root ensures that the dataset and model paths resolve correctly.

## Limitations
- The dataset is simulated, so results may not generalize to real industrial equipment.
- Machine failures are rare, making precision, recall, F1-score, and average precision important evaluation metrics alongside accuracy.
- Threshold selection involves a trade-off between detecting failures and generating false alarms.
- Further validation on real operational data is required before any industrial deployment.

## Future Improvements
- Evaluate additional classification algorithms.
- Perform systematic hyperparameter tuning.
- Analyze the cost of false negatives and false positives.
- Build a Django dashboard for interactive failure-risk predictions.
- Validate the model on real-world equipment data when available.

## Author
**Aspiring Data Scientist | Python | Machine Learning | Data Analysis**

GitHub: [SundheepVayyavuru](https://github.com/SundheepVayyavuru)