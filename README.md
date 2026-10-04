# ML Learning

A collection of Jupyter notebooks documenting a hands-on journey through data analysis and machine learning. The notebooks cover data cleaning, exploratory data analysis, feature engineering, supervised learning, model tuning, ensemble methods, and unsupervised learning.

## Learning path

Follow the notebooks in this order for a gradual introduction. Each notebook is self-contained; later notebooks do not require saved output from earlier ones.

| Step | Notebook | Topics and data |
|---:|---|---|
| 1 | [`cleaning and preprocessing heart_data.ipynb`](<cleaning and preprocessing heart_data.ipynb>) | Heart disease data: EDA, data cleaning, categorical encoding, scaling, and feature preparation. Uses `heart.csv`. |
| 2 | [`eda_cleaning_preprocessing_fe&fs.ipynb`](<eda_cleaning_preprocessing_fe&fs.ipynb>) | Insurance data: EDA, duplicate handling, encoding, BMI feature engineering, scaling, correlation, and chi-square feature selection. Uses `insurance.csv`. |
| 3 | [`linear_regression.ipynb`](<linear_regression.ipynb>) | Insurance data: preprocessing and feature selection followed by a linear regression model and R² evaluation. Uses `insurance.csv`. |
| 4 | [`logistic_knn_naive_bayes_Decision_tree_SVM.ipynb`](<logistic_knn_naive_bayes_Decision_tree_SVM.ipynb>) | Titanic survival classification: logistic regression, K-nearest neighbors, Naive Bayes, decision tree, SVM, and cross-validation. |
| 5 | [`hyper_para_tunning.ipynb`](<hyper_para_tunning.ipynb>) | Iris classification: KNN and SVM examples, then grid and randomized search for SVM parameters. |
| 6 | [`ensemble_learnings.ipynb`](<ensemble_learnings.ipynb>) | Iris classification: stacking, random forest, AdaBoost, gradient boosting, and XGBoost. |
| 7 | [`unsupervised_learnings.ipynb`](<unsupervised_learnings.ipynb>) | Unsupervised learning with generated datasets: K-means, DBSCAN, and principal component analysis (PCA). |

## Datasets

- [`heart.csv`](heart.csv) — heart disease data used by the heart preprocessing notebook.
- [`insurance.csv`](insurance.csv) — medical insurance data used by the EDA and linear regression notebooks.
- The classification and tuning notebooks load the Titanic and Iris sample datasets with `seaborn.load_dataset()`. Seaborn may need an internet connection to download these datasets the first time they are used.
- The unsupervised learning notebook generates its example data within the notebook; it does not need a CSV file.

## Set up and run

You need Python and Jupyter Notebook. From the repository folder, create and activate a virtual environment, then install the libraries used across the notebooks:

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Or on macOS/Linux:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib seaborn scikit-learn scipy xgboost notebook
```

Start Jupyter from the repository folder:

```bash
jupyter notebook
```

Open a notebook from the learning path above and run its cells from top to bottom. Keeping Jupyter's working directory at the repository root lets the notebooks find `heart.csv` and `insurance.csv` by their relative filenames. XGBoost is used only in the ensemble notebook.

## Repository contents

```text
ML-learnings-/
├── README.md
├── heart.csv
├── insurance.csv
├── cleaning and preprocessing heart_data.ipynb
├── eda_cleaning_preprocessing_fe&fs.ipynb
├── linear_regression.ipynb
├── logistic_knn_naive_bayes_Decision_tree_SVM.ipynb
├── hyper_para_tunning.ipynb
├── ensemble_learnings.ipynb
└── unsupervised_learnings.ipynb
```
