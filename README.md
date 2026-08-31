# House Price Prediction

A beginner-friendly machine learning project that predicts California housing prices with an XGBoost regression model. The project is implemented as a Jupyter notebook and walks through a typical supervised learning workflow: loading data, exploring the dataset, visualizing correlations, splitting features and target values, training a model, evaluating predictions, and plotting actual versus predicted prices.

## Project Overview

This repository contains a single notebook, `house_price_prediction.ipynb`, that uses the California Housing dataset from scikit-learn. The dataset includes district-level housing attributes such as median income, average rooms, population, and geographic coordinates. The target variable is the median house value for California districts, expressed in units of $100,000.

The notebook trains an `XGBRegressor` model from the XGBoost library and evaluates it with common regression metrics:

- **R² score**: Measures how much of the variance in house prices is explained by the model.
- **Mean Absolute Error (MAE)**: Measures the average absolute difference between predicted and actual values.

## Repository Contents

```text
.
├── README.md
└── house_price_prediction.ipynb
```

| File | Description |
| --- | --- |
| `house_price_prediction.ipynb` | Main notebook containing data loading, exploration, model training, evaluation, and visualization. |
| `README.md` | Project documentation, setup instructions, workflow details, and usage notes. |

## Dataset

The project uses `sklearn.datasets.fetch_california_housing()`, which downloads/loads the California Housing dataset through scikit-learn.

### Features

The model uses the following input columns:

| Feature | Meaning |
| --- | --- |
| `MedInc` | Median income in the block group. |
| `HouseAge` | Median house age in the block group. |
| `AveRooms` | Average number of rooms per household. |
| `AveBedrms` | Average number of bedrooms per household. |
| `Population` | Block group population. |
| `AveOccup` | Average number of household members. |
| `Latitude` | Block group latitude. |
| `Longitude` | Block group longitude. |

### Target

| Column | Meaning |
| --- | --- |
| `price` | Median house value in units of $100,000. |

### Dataset Shape

After adding the target column, the dataframe contains:

- **20,640 rows**
- **9 columns**: 8 input features plus the target price column

## Modeling Approach

The notebook follows these steps:

1. **Import dependencies**
   - NumPy
   - pandas
   - Matplotlib
   - Seaborn
   - scikit-learn
   - XGBoost

2. **Load the dataset**
   - Uses `fetch_california_housing()` from scikit-learn.
   - Converts the dataset into a pandas dataframe.
   - Adds the target variable as a `price` column.

3. **Explore the data**
   - Displays the first few rows.
   - Checks dataframe shape.
   - Checks for missing values.
   - Generates descriptive statistics.

4. **Analyze correlations**
   - Computes correlations between all columns.
   - Visualizes the correlation matrix with a Seaborn heatmap.

5. **Split features and target**
   - `X`: all feature columns.
   - `Y`: the `price` target column.

6. **Create training and test sets**
   - Uses an 80/20 train-test split.
   - Uses `random_state=2` for reproducibility.

7. **Train the model**
   - Builds an `XGBRegressor` model.
   - Fits the model on the training data.

8. **Evaluate performance**
   - Generates predictions on both training and test sets.
   - Calculates R² score and MAE.

9. **Visualize predictions**
   - Creates a scatter plot comparing actual training prices with predicted prices.

## Reported Results

The notebook output reports the following model metrics:

| Dataset | R² Score | Mean Absolute Error |
| --- | ---: | ---: |
| Training data | `0.943650140819218` | `0.1933648700612105` |
| Test data | `0.8338000331788725` | `0.3108631800268186` |

These results suggest that the model fits the training data strongly and generalizes reasonably well to unseen test data. The difference between train and test performance may indicate some overfitting, which could be explored further with hyperparameter tuning and cross-validation.

## Requirements

This project requires Python and the following Python packages:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `xgboost`
- `jupyter` or `notebook`

## Getting Started

### 1. Clone the repository

```bash
git clone <repository-url>
cd house_price_prediction
```

### 2. Create and activate a virtual environment

On macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost jupyter
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
house_price_prediction.ipynb
```

### 5. Run the notebook

Run the cells from top to bottom to reproduce the data exploration, model training, evaluation metrics, and visualization.

## How to Use the Notebook

1. Open `house_price_prediction.ipynb` in Jupyter Notebook, JupyterLab, VS Code, or another notebook-compatible editor.
2. Run the import cell first to load all dependencies.
3. Run the dataset loading cells to fetch and inspect the California Housing dataset.
4. Continue through the exploratory data analysis cells to understand missing values, summary statistics, and correlations.
5. Run the train-test split and model training cells.
6. Review the evaluation output for training and test performance.
7. Inspect the scatter plot to compare actual prices and model predictions visually.

## Possible Improvements

Future improvements could include:

- Adding a `requirements.txt` file for reproducible dependency installation.
- Moving notebook logic into reusable Python scripts or modules.
- Adding cross-validation for more robust model evaluation.
- Tuning XGBoost hyperparameters such as `n_estimators`, `max_depth`, `learning_rate`, and `subsample`.
- Comparing XGBoost against other regressors, such as linear regression, random forest, and gradient boosting models.
- Adding feature importance analysis.
- Saving the trained model with `joblib` or `pickle` for later inference.
- Adding a command-line interface or simple web app for making predictions from new housing inputs.

## Notes

- The notebook markdown says "Boston House Price Dataset" in one section, but the code loads the California Housing dataset with `fetch_california_housing()`.
- The target values are not raw dollar prices; they are expressed in units of $100,000.
- If the dataset is not already cached locally, scikit-learn may need internet access the first time it is fetched.

## License

No license file is currently included in this repository. Add a license before distributing or reusing the project publicly.
