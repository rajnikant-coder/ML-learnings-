# 🤖 ML Learning Journey

This repository contains my hands-on **Machine Learning practice notebooks**. It follows a learning path from data exploration and preprocessing to regression, classification, model tuning, ensemble methods, and unsupervised learning using Python.

## 📚 Notebooks

| # | Project | Type | Main Topics / Models |
|---|---|---|---|
| 1 | ❤️ Heart Data Cleaning & Preprocessing | Data preparation | EDA, invalid-value handling, encoding, scaling |
| 2 | 🏥 Insurance EDA, Feature Engineering & Selection | Data preparation | EDA, cleaning, BMI categories, correlation, chi-square |
| 3 | 💰 Insurance Cost Prediction | Regression | Linear Regression, R² and adjusted R² |
| 4 | 🚢 Titanic Survival Prediction | Classification | Logistic Regression, KNN, Naive Bayes, Decision Tree, SVM |
| 5 | 🌸 Hyperparameter Tuning | Model selection | KNN, SVM, Grid Search CV, Randomized Search CV |
| 6 | 🌳 Ensemble Learning | Ensemble classification | Stacking, Random Forest, AdaBoost, Gradient Boosting, XGBoost |
| 7 | 🔵 Unsupervised Learning | Clustering and dimensionality reduction | K-Means, DBSCAN, PCA |

The suggested order is the order shown above. Each notebook can be opened and run independently; notebooks do not pass saved results to one another.

---

# ❤️ 1. Heart Data Cleaning & Preprocessing

## 📌 Overview

This notebook explores and prepares a heart disease dataset. It demonstrates data inspection and visualization, checks for data quality issues, handles zero values in selected measurements, encodes categorical features, and scales numerical features.

## 📊 Dataset

The notebook uses [`heart.csv`](heart.csv), containing **918 rows and 12 columns**. The target column is `HeartDisease`.

| Feature | Description |
|---|---|
| `Age` | Age |
| `Sex` | Sex |
| `ChestPainType` | Chest pain type |
| `RestingBP` | Resting blood pressure |
| `Cholesterol` | Cholesterol level |
| `FastingBS` | Fasting blood sugar |
| `RestingECG` | Resting ECG result |
| `MaxHR` | Maximum heart rate |
| `ExerciseAngina` | Exercise-induced angina |
| `Oldpeak` | ST depression |
| `ST_Slope` | ST slope |
| `HeartDisease` | Target variable |

## 🔍 Workflow

- Inspect the dataset, data types, summary statistics, missing values, and duplicates.
- Visualize target and feature distributions, relationships, and correlations.
- Replace zero values in `Cholesterol` and `RestingBP` with the mean of non-zero observations.
- One-hot encode categorical columns.
- Apply `StandardScaler` to numerical columns.

Notebook: [`cleaning and preprocessing heart_data.ipynb`](<cleaning and preprocessing heart_data.ipynb>)

---

# 🏥 2. Insurance EDA, Feature Engineering & Feature Selection

## 📌 Overview

This notebook explores and prepares insurance data, engineers BMI categories, and demonstrates correlation and chi-square approaches to feature analysis.

## 📊 Dataset

The notebook uses [`insurance.csv`](insurance.csv), which contains **1,338 rows and 7 columns** before duplicate removal. The target is `charges`.

| Feature | Description |
|---|---|
| `age` | Age |
| `sex` | Sex |
| `bmi` | Body Mass Index |
| `children` | Number of children |
| `smoker` | Smoking status |
| `region` | Residential region |
| `charges` | Insurance charges / target |

## 🔍 Workflow

- Inspect the data, distributions, missing values, and correlations.
- Remove duplicate rows; the notebook reports 1,337 rows after this step.
- Encode `sex`, `smoker`, and `region`.
- Create BMI categories and one-hot encode them.
- Standardize selected numerical features.
- Examine feature relationships with `charges` using Pearson correlation and chi-square tests on binned charges.

Notebook: [`eda_cleaning_preprocessing_fe&fs.ipynb`](<eda_cleaning_preprocessing_fe&fs.ipynb>)

---

# 💰 3. Insurance Cost Prediction with Linear Regression

## 📌 Overview

This notebook uses the insurance data to build a regression model for predicting `charges`. It includes EDA and preprocessing, creates encoded and scaled features, selects a feature set, and evaluates a `LinearRegression` model with R² and adjusted R².

The notebook makes its own data preparation steps and reads [`insurance.csv`](insurance.csv); it does not require running notebook 2 first.

Notebook: [`linear_regression.ipynb`](<linear_regression.ipynb>)

---

# 🚢 4. Titanic Survival Classification

## 📌 Overview

This notebook compares several classifiers for predicting passenger survival. The notebook prepares the data, handles missing values, encodes categorical columns, and reports classification metrics and cross-validation scores.

## 🤖 Models

1. Logistic Regression
2. K-Nearest Neighbors (KNN)
3. Naive Bayes
4. Decision Tree
5. Support Vector Machine (SVM)

The notebook loads the Titanic sample dataset through `seaborn.load_dataset("titanic")`.

Notebook: [`logistic_knn_naive_bayes_Decision_tree_SVM.ipynb`](<logistic_knn_naive_bayes_Decision_tree_SVM.ipynb>)

---

# 🌸 5. Hyperparameter Tuning

## 📌 Overview

Using the Iris sample dataset, this notebook demonstrates baseline KNN and SVM models, followed by SVM parameter search with `GridSearchCV` and `RandomizedSearchCV`.

The Iris data is loaded through `seaborn.load_dataset("iris")`.

Notebook: [`hyper_para_tunning.ipynb`](<hyper_para_tunning.ipynb>)

---

# 🌳 6. Ensemble Learning

## 📌 Overview

This notebook uses the Iris sample dataset to practice combining and comparing classification models.

## 🤖 Methods

- Stacking with decision tree, SVM, and logistic regression base learners
- Random Forest
- AdaBoost
- Gradient Boosting
- XGBoost

The notebook loads Iris through Seaborn. XGBoost is used only in this notebook.

Notebook: [`ensemble_learnings.ipynb`](<ensemble_learnings.ipynb>)

---

# 🔵 7. Unsupervised Learning

## 📌 Overview

This notebook introduces clustering and dimensionality reduction with generated example datasets, so it does not depend on the CSV files.

## 🧠 Methods

- K-Means clustering on generated blob data
- K-Means and DBSCAN comparison on generated moon-shaped data
- Principal Component Analysis (PCA) to project generated multi-feature data into two dimensions

Notebook: [`unsupervised_learnings.ipynb`](<unsupervised_learnings.ipynb>)

---

# 🛠️ Technologies Used

### Programming Language

- Python

### Libraries

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- SciPy
- XGBoost
- Jupyter Notebook

### Concepts Practiced

- Exploratory Data Analysis
- Data cleaning and preprocessing
- Categorical encoding and feature scaling
- Feature engineering and feature selection
- Regression and classification
- Cross-validation and hyperparameter search
- Ensemble learning
- Clustering and dimensionality reduction

---

# 📂 Repository Structure

```text
ML learning/
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

> Keep dataset files in the repository only when their licensing and redistribution terms allow it.

---

# 🚀 How to Run

## 1. Open the repository folder

Open a terminal in the repository root, where the notebooks and CSV files are located.

## 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

## 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib seaborn scikit-learn scipy xgboost notebook
```

## 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open a notebook and run its cells from top to bottom. Run Jupyter from the repository root so notebooks can locate `heart.csv` and `insurance.csv` using their relative paths. The Titanic and Iris notebooks load sample data through Seaborn and may need an internet connection on first use.

---

# 🎯 Learning Objectives

Through these notebooks, I practiced:

- Exploring datasets and communicating patterns with visualizations
- Finding and addressing missing, duplicate, and invalid values
- Encoding categorical variables and scaling numerical features
- Creating features and assessing their usefulness
- Training and evaluating regression and classification models
- Comparing cross-validation and parameter search methods
- Combining models with ensemble methods
- Applying clustering and PCA to unlabeled data

---

## 👨‍💻 Author

**Rajnikant**

Machine Learning & Data Science Learner

---

⭐ These notebooks document my ongoing machine learning learning journey. Explore them in order or open the topic you want to practice.
