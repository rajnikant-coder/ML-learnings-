# 📊 Data Preprocessing, EDA, Feature Engineering & Feature Selection

This repository contains practical **Data Science / Machine Learning preprocessing projects** focused on understanding raw datasets and preparing them for machine learning.

The notebooks demonstrate an end-to-end preprocessing workflow including:

- Exploratory Data Analysis (EDA)
- Data inspection and descriptive statistics
- Missing-value analysis
- Duplicate detection and removal
- Data cleaning
- Categorical encoding
- Feature engineering
- Feature scaling
- Correlation analysis
- Pearson correlation
- Chi-square statistical testing
- Feature selection

> **Note:** These notebooks focus on data preparation and feature analysis. They do not contain a final machine learning model-training/evaluation stage.

---

# 📚 Projects

| # | Project | Dataset | Main Focus |
|---|---|---|---|
| 1 | 🏥 Heart Data EDA, Cleaning & Preprocessing | `heart.csv` | EDA, data cleaning, encoding & scaling |
| 2 | 🏥 Insurance Data EDA, Cleaning, Preprocessing, FE & FS | `insurance.csv` | EDA, cleaning, feature engineering & feature selection |

---

# 🏥 1. Heart Data — EDA, Cleaning & Preprocessing

## 📌 Overview

This notebook performs exploratory data analysis, data cleaning, and preprocessing on a heart disease dataset.

The workflow starts with understanding the dataset and its distributions, identifies invalid zero values, performs categorical encoding, and finally scales selected numerical features using `StandardScaler`.

## 📊 Dataset

The notebook loads:

```python
df = pd.read_csv("heart.csv")
```

### Dataset dimensions

```text
918 rows × 12 columns
```

### Features

| Feature | Description |
|---|---|
| `Age` | Age |
| `Sex` | Sex |
| `ChestPainType` | Chest pain type |
| `RestingBP` | Resting blood pressure |
| `Cholesterol` | Cholesterol level |
| `FastingBS` | Fasting blood sugar |
| `RestingECG` | Resting ECG |
| `MaxHR` | Maximum heart rate |
| `ExerciseAngina` | Exercise-induced angina |
| `Oldpeak` | ST depression |
| `ST_Slope` | ST slope |
| `HeartDisease` | Heart disease target |

## 🔍 Exploratory Data Analysis

The notebook performs:

- Dataset shape inspection
- Column inspection
- Data-type inspection
- Descriptive statistics
- Duplicate-value checking
- Missing-value checking
- Target distribution visualization
- Numerical feature distributions
- Categorical feature analysis
- Box plots
- Correlation heatmap

### Numerical Features Visualized

The notebook examines the distributions of:

```text
Age
RestingBP
Cholesterol
MaxHR
```

It also analyzes relationships involving:

- Sex
- Chest pain type
- Fasting blood sugar
- Cholesterol
- Heart disease

## 🧹 Data Cleaning

The notebook identifies zero values in `Cholesterol` and `RestingBP`.

Instead of keeping these zero values, their replacement values are calculated using the mean of the **non-zero observations**.

### Cholesterol

```python
ch_mean = df.loc[df['Cholesterol'] != 0, 'Cholesterol'].mean()

df['Cholesterol'] = df['Cholesterol'].replace(0, ch_mean)
df['Cholesterol'] = df['Cholesterol'].round(2)
```

### Resting Blood Pressure

```python
resting_bp_mean = df.loc[df['RestingBP'] != 0, 'RestingBP'].mean()

df['RestingBP'] = df['RestingBP'].replace(0, resting_bp_mean)
df['RestingBP'] = df['RestingBP'].round(2)
```

## 🔄 Data Preprocessing

### One-Hot Encoding

Categorical features are converted using:

```python
pd.get_dummies(df, drop_first=True)
```

The encoded dataframe is then converted to integer values.

### Feature Scaling

`StandardScaler` is applied to:

```text
Age
RestingBP
Cholesterol
MaxHR
Oldpeak
```

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df_encode[numerical_cols] = scaler.fit_transform(
    df_encode[numerical_cols]
)
```

## 🎯 Outcome

The notebook produces a cleaned and transformed dataset suitable for use in subsequent machine learning workflows.

---

# 🏥 2. Insurance Data — EDA, Cleaning, Preprocessing, Feature Engineering & Feature Selection

## 📌 Overview

This notebook works with an insurance dataset and demonstrates a broader preprocessing workflow.

It covers:

```text
EDA
↓
Data Cleaning
↓
Categorical Encoding
↓
Feature Engineering
↓
Feature Scaling
↓
Correlation Analysis
↓
Chi-Square Feature Selection
```

## 📊 Dataset

The notebook loads:

```python
df = pd.read_csv("insurance.csv")
```

### Dataset dimensions

```text
1338 rows × 7 columns
```

After duplicate removal:

```text
1337 rows × 7 columns
```

### Features

| Feature | Description |
|---|---|
| `age` | Age |
| `sex` | Sex |
| `bmi` | Body Mass Index |
| `children` | Number of children |
| `smoker` | Smoking status |
| `region` | Residential region |
| `charges` | Insurance charges / target |

---

## 🔍 Exploratory Data Analysis

The notebook performs:

- Dataset shape inspection
- Head/data preview
- Dataset information
- Descriptive statistics
- Missing-value checking
- Column inspection
- Numerical feature distributions
- Categorical feature distributions
- Box plots
- Correlation heatmap

### Numerical Features

The distributions of the following variables are explored:

```text
age
bmi
children
charges
```

Categorical variables analyzed include:

```text
sex
smoker
children
```

---

# 🧹 Data Cleaning

A copy of the original dataframe is created:

```python
df_cleaned = df.copy()
```

## Duplicate Removal

Duplicate rows are removed using:

```python
df_cleaned.drop_duplicates(inplace=True)
```

The dataset changes from:

```text
1338 rows → 1337 rows
```

## Missing Values

Missing values are checked using:

```python
df_cleaned.isnull().sum()
```

The notebook does not record missing values requiring imputation.

---

# 🔤 Categorical Encoding

## Sex

The `sex` feature is converted into a binary representation:

```python
df_cleaned['sex'] = df_cleaned['sex'].map({
    "male": 0,
    "female": 1
})
```

The column is renamed:

```text
sex → is_female
```

## Smoker

The `smoker` feature is converted into:

```text
no  → 0
yes → 1
```

and renamed:

```text
smoker → is_smoker
```

## Region

One-hot encoding is applied to `region`:

```python
df_cleaned = pd.get_dummies(
    df_cleaned,
    columns=['region'],
    drop_first=True
)
```

This creates encoded regional features such as:

```text
region_northwest
region_southeast
region_southwest
```

---

# 🧬 Feature Engineering

A new feature is created from `bmi`.

## BMI Category

BMI is divided into four categories using:

```python
pd.cut(
    df_cleaned['bmi'],
    bins=[0, 18.5, 24.9, 29.9, float('inf')],
    labels=['uw', 'n', 'ow', 'obese']
)
```

The categories represent:

```text
uw    → Underweight
n     → Normal
ow    → Overweight
obese → Obese
```

The resulting categorical feature is then one-hot encoded.

---

# ⚖️ Feature Scaling

`StandardScaler` is applied to:

```text
age
bmi
children
```

```python
from sklearn.preprocessing import StandardScaler

cols = ['age', 'bmi', 'children']

scaler = StandardScaler()
df_cleaned[cols] = scaler.fit_transform(df_cleaned[cols])
```

This transforms the numerical features to a standardized scale.

---

# 📈 Feature Selection

The notebook uses two statistical approaches:

1. Pearson Correlation
2. Chi-Square Test

---

## 1. Pearson Correlation

Pearson correlation is calculated between selected features and:

```text
charges
```

The recorded correlations are:

| Feature | Pearson Correlation |
|---|---:|
| `is_smoker` | 0.787234 |
| `age` | 0.298309 |
| `bmi_category_obese` | 0.200348 |
| `bmi` | 0.196236 |
| `region_southeast` | 0.073577 |
| `children` | 0.067390 |
| `region_northwest` | -0.038695 |
| `region_southwest` | -0.043637 |
| `is_female` | -0.058046 |
| `bmi_category_n` | -0.104042 |
| `bmi_category_ow` | -0.120601 |

The notebook uses these correlation values to examine the relationship between individual features and insurance charges.

---

# 2. Chi-Square Feature Selection

For categorical features, the notebook applies a **Chi-Square test of independence**.

The target `charges` is first divided into four quantile-based groups:

```python
df_cleaned['charges_bin'] = pd.qcut(
    df_cleaned['charges'],
    q=4,
    labels=False
)
```

The significance level is:

```python
alpha = 0.05
```

The notebook evaluates the categorical features against the binned target.

### Recorded Results

| Feature | Chi-Square Statistic | p-value | Notebook Decision |
|---|---:|---:|---|
| `is_smoker` | 848.219178 | 1.507478e-183 | Reject Null (Keep Feature) |
| `region_southeast` | 15.998167 | 1.134966e-03 | Reject Null (Keep Feature) |
| `is_female` | 10.258784 | 1.648974e-02 | Reject Null (Keep Feature) |
| `bmi_category_obese` | 8.515711 | 3.647336e-02 | Reject Null (Keep Feature) |
| `region_southwest` | 5.091893 | 1.651906e-01 | Accept Null (Drop Feature) |
| `bmi_category_ow` | 4.251490 | 2.355571e-01 | Accept Null (Drop Feature) |
| `bmi_category_n` | 3.708088 | 2.947595e-01 | Accept Null (Drop Feature) |
| `region_northwest` | 1.134240 | 7.688154e-01 | Accept Null (Drop Feature) |

> The "Decision" column above reproduces the decision labels generated by the notebook's `alpha = 0.05` rule.

---

# 🛠️ Technologies & Libraries

## Programming Language

- Python

## Data Analysis

- NumPy
- Pandas

## Data Visualization

- Matplotlib
- Seaborn

## Machine Learning / Preprocessing

- Scikit-learn
- `StandardScaler`

## Statistical Analysis

- SciPy
- Pearson correlation
- Chi-Square test

---

# 📂 Suggested Repository Structure

```text
ML-Data-Preprocessing/
│
├── README.md
│
├── Heart-Data-Preprocessing/
│   ├── cleaning_and_preprocessing_heart_data.ipynb
│   └── heart.csv
│
└── Insurance-EDA-Preprocessing/
    ├── eda_cleaning_preprocessing_fe_fs.ipynb
    └── insurance.csv
```

> Dataset files should only be committed if their respective licenses and redistribution terms permit it.

---

# 🚀 How to Run

## 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

## 2. Navigate to the project

```bash
cd ML-Data-Preprocessing
```

## 3. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy jupyter
```

## 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Then open the required notebook.

Make sure the corresponding CSV dataset is available in the location expected by the notebook.

---

# 🎯 Skills Practiced

These projects demonstrate practical understanding of:

- Exploratory Data Analysis
- Data quality inspection
- Missing-value analysis
- Duplicate handling
- Invalid-value treatment
- Categorical encoding
- One-hot encoding
- Feature engineering
- Feature scaling
- Data visualization
- Correlation analysis
- Pearson correlation
- Chi-Square hypothesis testing
- Statistical feature selection
- Preparing datasets for machine learning

---

# 📌 Project Status

| Project | Status |
|---|---|
| Heart Data EDA & Preprocessing | ✅ Completed |
| Insurance EDA, Preprocessing, FE & FS | ✅ Completed |

---

## 👨‍💻 Author

**Rajnikant**

Machine Learning & Data Science Enthusiast

---

⭐ This repository represents practical work in **EDA, data cleaning, preprocessing, feature engineering, and feature selection** as part of my Machine Learning learning journey.
    