# Predictive Maintenance & Machine Failure Prediction

## Dataset
- **Name:** AI4I 2020 Predictive Maintenance Dataset
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)
- **Records:** 10,000
- **Original columns:** 14
- **Target:** `Machine failure`

The dataset contains machine type, air temperature, process temperature, rotational speed, torque, tool wear, and machine failure information.

**Note:** This is a simulated dataset. The results demonstrate a machine-learning workflow and do not establish real-world industrial performance.

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
The threshold was selected on a validation set to maximize precision while maintaining validation recall of at least 80%.

- Selected threshold: 0.2567
- Test failure-class precision: 46%
- Test failure-class recall: 85%
- Test failure-class F1-score: 59%
- Test accuracy: Approximately 96%
- Test average precision: 0.7575

The tuned threshold improves failure detection but increases false alarms. Average precision remains unchanged because the underlying probability scores are unchanged.

## How to Run
1. Clone or download this repository.
2. Create and activate a Python virtual environment.
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Download the dataset from the UCI Machine Learning Repository.
5. Place `ai4i2020.csv` inside the `data/` directory.
6. Launch Jupyter Notebook from the project root and open `notebooks/01_data_exploration.ipynb`.

The notebook uses relative paths, so launch Jupyter from the project root to ensure the dataset and model paths resolve correctly.