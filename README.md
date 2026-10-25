# Medical Insurance Cost Prediction

A machine learning project that predicts individual medical insurance charges using the Medical Cost Personal Dataset. The project covers data preparation, exploratory data analysis, feature engineering, model comparison, hyperparameter tuning, evaluation, and feature importance analysis.

## Project Overview

**Objective:** Predict medical insurance charges (`charges`) using demographic and health-related characteristics.

**Dataset:** Medical Cost Personal Dataset, Kaggle.

**Problem type:** Supervised learning, Regression.

**Final model:** XGBoost Regressor, selected based on the lowest tuned cross-validation RMSE.

**Tools and technologies:**
- Python
- pandas and NumPy
- scikit-learn
- XGBoost and LightGBM
- Matplotlib and Seaborn
- VS Code and Jupyter notebooks
- Git and GitHub

## Dataset

The dataset contains 1,338 observations and 7 columns, including the target variable `charges`.

The features describe different aspects of individuals, including:
- Age and sex
- Body Mass Index (BMI)
- Number of children or dependents
- Smoking status
- Residential region

**Target variable:** `charges`, the individual medical costs billed by health insurance.

**Dataset source:** [Kaggle: Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance)

Download the dataset from Kaggle and place the CSV file in the project's `data/raw/` directory using the filename expected by the notebooks.

## Project Workflow

The project follows a typical machine learning workflow:

1. **Data loading**: Load the dataset into pandas DataFrames.
2. **Data inspection**: Examine the shape, data types, summary statistics, missing values, duplicates, and target distribution.
3. **Exploratory data analysis**: Investigate relationships between individual characteristics and insurance charges.
4. **Data cleaning**: Check duplicates, data quality, and numerical and categorical columns.
5. **Feature engineering**: Create features such as `bmi_category`, `age_group`, `smoker_bmi`, `smoker_age`, and `smoker_children`.
6. **Data splitting**: Separate training and testing data using an 80/20 split.
7. **Preprocessing**: Apply appropriate categorical encoding, numerical scaling where required, and preprocessing pipelines.
8. **Model training**: Train and compare multiple regression algorithms.
9. **Model evaluation**: Compare performance using 5-fold cross-validation and test-set metrics.
10. **Hyperparameter tuning**: Search for better model settings using GridSearchCV.
11. **Feature importance**: Use permutation importance to investigate the contribution of input features to predictive performance.
12. **Model selection**: Select the model with the lowest tuned cross-validation RMSE.

## Models Compared

The following regression algorithms were evaluated:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Elastic Net
- Random Forest Regressor
- Gradient Boosting Regressor
- XGBoost Regressor
- LightGBM Regressor
- K-Nearest Neighbors Regressor
- Support Vector Regression (SVR)

The final model was selected based on its tuned cross-validation RMSE.

## Model Performance

The XGBoost Regressor was selected as the final model based on its lowest tuned cross-validation RMSE. LightGBM achieved slightly better results on the held-out test set.

### Initial Model

| Metric | Result |
|---|---:|
| Cross-validation RMSE | 5,428.08 |
| Cross-validation RMSE standard deviation | 262.89 |
| Test RMSE | 4,979.57 |
| Test MAE | 2,766.21 |
| Test R² | 0.865059 |

### Tuned Model

The selected hyperparameters were determined through GridSearchCV. Refer to the experiment results and saved model configuration for the exact parameter values.

| Metric | Result |
|---|---:|
| Cross-validation RMSE | 4,548.87 |
| Test RMSE | 4,300.89 |
| Test MAE | 2,461.80 |
| Test R² | 0.899336 |

### Interpreting the Results

- **RMSE:** Measures prediction error, penalizing larger errors more heavily. Lower is better.
- **MAE:** Measures the average absolute difference between predicted and actual insurance charges. Lower is better.
- **R²:** Measures the proportion of target variance explained by the model relative to a mean-prediction baseline. Higher is generally better.

Hyperparameter tuning reduced the XGBoost cross-validation RMSE by approximately 16.22%. The tuned model also improved its test-set RMSE, MAE, and R² compared with the initial model.

LightGBM achieved the best test-set metrics among the tuned models:

| Metric | Result |
|---|---:|
| Cross-validation RMSE | 4,559.38 |
| Test RMSE | 4,259.44 |
| Test MAE | 2,436.19 |
| Test R² | 0.901267 |

All error values are expressed in the same currency units as the dataset's `charges` target.

## Feature Importance

Permutation importance was used to investigate which input features most affected the model's predictive performance.

The numerical feature-importance rankings and values are not included here because the final permutation-importance results were not provided in the project information.

**Important:** Permutation importance measures predictive usefulness, not causation. It does not prove that changing a feature will cause a particular change in insurance charges.

## Project Structure

The following is a suggested structure. Adjust the paths to match the files in your repository.

```text
medical-insurance-cost-prediction/
├── data/
│   ├── raw/
│   │   └── medical_insurance_raw.csv
│   ├── external/
│   └── processed/
├── notebooks/
│   └── medical_insurance_cost_prediction.ipynb
├── models/
│   └── best_regression_model.joblib
├── outputs/
│   ├── figures/
│   └── tables/
├── src/
├── requirements.txt
├── .gitignore
└── README.md
```

- `data/` — Dataset files or instructions for obtaining them.
- `notebooks/` — Notebooks containing analysis and experiments.
- `models/` — Saved model artifacts, if included.
- `outputs/tables/` — Generated evaluation tables and model comparison results.
- `src/` — Reusable Python modules, if the project uses them.
- `requirements.txt` — Python package dependencies.
- `.gitignore` — Files and directories that Git should not track.
- `README.md` — Project documentation.

Only include directories and filenames that actually exist in the repository. Large datasets and generated model files may be better kept outside Git or managed using an appropriate data-versioning approach.

## Getting Started

### 1. Install Prerequisites

Install:
- Git
- Python 3.12 or another compatible Python version
- VS Code or JupyterLab

Verify that Python and Git are available:

```bash
python --version
git --version
```

### 2. Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/YOUR_USERNAME/medical-insurance-cost-prediction.git
cd medical-insurance-cost-prediction
```

Replace the example GitHub URL with the actual URL of your repository.

Cloning an existing repository already configures the remote named `origin`. You do not need to run `git init` or `git remote add origin` after cloning.

### 3. Create a Virtual Environment

Create a project-specific virtual environment:

```bash
python -m venv .venv
```

A virtual environment isolates this project's Python packages from other projects and the system-wide Python installation.

### 4. Activate the Virtual Environment

**Windows PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

**Git Bash:**

```bash
source .venv/Scripts/activate
```

After activation, your terminal will usually display `(.venv)` at the beginning of the command prompt.

If PowerShell blocks activation because of its execution policy, you can use Git Bash or consult the official Python documentation for the appropriate activation guidance.

### 5. Verify the Environment

With the virtual environment activated, run:

```bash
python --version
where.exe python
python -m pip --version
```

On Windows, `where.exe python` should list the virtual environment's Python executable first.

The `python -m pip --version` command should also indicate that pip belongs to the virtual environment.

### 6. Install Dependencies

Upgrade pip within the active virtual environment:

```bash
python -m pip install --upgrade pip
```

Install the project's dependencies:

```bash
python -m pip install -r requirements.txt
```

**Important:** Always activate `.venv` before installing packages, and use `python -m pip` instead of a standalone `pip` command. This helps ensure that packages are installed into the intended Python environment.

If the repository does not yet contain `requirements.txt`, install the necessary packages:

```bash
python -m pip install pandas numpy scikit-learn matplotlib seaborn joblib xgboost lightgbm jupyter
```

Then generate the dependency file:

```bash
python -m pip freeze > requirements.txt
```

Review the generated file before committing it. Ideally, it should reflect the packages required by the project rather than unrelated packages installed in the environment.

### 7. Open the Notebook

With the virtual environment activated, open the project in VS Code and select the `.venv` Python environment as the notebook kernel.

Alternatively, launch Jupyter:

```bash
python -m jupyter lab
```

Open the notebook associated with the project and execute the cells in their intended order.

### 8. Obtain the Dataset

Download the dataset from the [Kaggle Medical Cost Personal Dataset page](https://www.kaggle.com/datasets/mirichoi0218/insurance).

Place the CSV file in `data/raw/` using the filename expected by the notebook. If the dataset is not included in the repository, ensure that the download instructions and expected path are documented.

## Reproducibility

For consistent results:

- Use the documented Python environment and dependencies.
- Set the random seed to `42` where supported.
- Keep training and test data separate.
- Fit preprocessing steps using training data only.
- Use 5-fold cross-validation for model comparison and hyperparameter tuning.
- Evaluate the final selected model on held-out test data.
- Record the model parameters and evaluation metrics.

Results can vary if package versions, random seeds, data splits, or preprocessing procedures differ.

## Limitations and Future Improvements

Potential improvements include:

- Testing additional feature-engineering approaches and feature interactions.
- Investigating target transformations to address the right-skewed distribution of `charges`.
- Examining residuals and prediction errors across different insurance-charge ranges.
- Comparing additional hyperparameter search strategies.
- Evaluating model stability across different data splits.
- Saving the complete preprocessing and prediction pipeline.
- Building a simple interface or API for medical insurance cost predictions.

The model's performance on the original test split does not guarantee equivalent performance on future insurance data or other populations.

## References

- [Kaggle: Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance)
- [Python Documentation](https://docs.python.org/3/)
- [Python `venv` Documentation](https://docs.python.org/3/library/venv.html)
- [pip Documentation](https://pip.pypa.io/en/stable/)
- [pandas Documentation](https://pandas.pydata.org/docs/)
- [NumPy Documentation](https://numpy.org/doc/)
- [scikit-learn Documentation](https://scikit-learn.org/stable/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [LightGBM Documentation](https://lightgbm.readthedocs.io/)
- [Matplotlib Documentation](https://matplotlib.org/stable/)
- [Seaborn Documentation](https://seaborn.pydata.org/)

## Author

**Samuel Ablordeppey**

GitHub: `https://github.com/samuelablorh`