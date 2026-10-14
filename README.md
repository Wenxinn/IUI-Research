# Touch-Based Continuous Authentication Using Machine Learning

**Machine Learning Research | Waseda University**

An experimental machine learning project investigating smartphone user authentication through touch-stroke behavior, with a focus on improving classification performance using feature selection.

**Keywords:** `Python` · `Machine Learning` · `Random Forest` · `Scikit-learn` · `Feature Selection` · `Behavioral Biometrics` · `Data Analysis`

---

## Overview

Traditional smartphone authentication methods, such as passwords, PINs, and fingerprint recognition, typically verify a user's identity at specific moments. However, they do not continuously verify whether the person operating the device is still the authorized user.

This research explores **touch-based continuous authentication**, a behavioral biometric approach that identifies users through their touchscreen interaction patterns.

By analyzing characteristics such as touch duration, velocity, acceleration, direction, and pressure, machine learning models can distinguish legitimate users from unauthorized users.

The primary objective was to develop and evaluate a Random Forest-based authentication model and investigate whether feature-selection techniques could improve classification performance.

## Key Results

The best-performing method, **Top 10 Feature Selection**, reduced the average Equal Error Rate (EER) from **9.222% to 8.876%**.

- **41 users** included in the research dataset
- **26 extracted touch-stroke features**
- **3 feature-selection approaches** evaluated
- **3.75% relative reduction in average EER** compared with the baseline
- Statistically significant differences from the baseline (paired t-test, p < 0.05)

A lower EER indicates better authentication performance.

## Technologies Used

| Category | Technologies |
|---|---|
| Programming | Python |
| Data Processing | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Classification | Random Forest |
| Feature Selection | Feature Importance, ExtraTreesClassifier |
| Evaluation | Equal Error Rate (EER), FAR, FRR |
| Statistical Analysis | SciPy, Paired t-tests |
| Visualization | Matplotlib, Seaborn |
| Development Environment | Jupyter Notebook |

## Dataset

The research used touch-stroke data collected from **41 smartphone users**, containing 26 extracted behavioral features.

Examples include:

- Stroke duration and inter-stroke time
- Starting and ending touch coordinates
- Stroke direction and trajectory length
- Touch velocity and acceleration
- Pressure-related measurements
- Device orientation

The dataset includes horizontal and vertical touch strokes.

These behavioral characteristics were used to distinguish legitimate users from other users during authentication.

## Methodology

The experimental workflow consisted of four main stages.

### 1. Data Preprocessing

The touch-stroke data was prepared for machine learning through:

- Filtering touch interactions using stroke duration
- Handling missing values and outliers
- Identifying stroke direction
- Applying min-max normalization to scale numerical features between 0 and 1

### 2. Dataset Construction

The authentication problem was formulated as a binary classification task:

- **Legitimate user (positive):** The authorized smartphone owner
- **Illegitimate user (negative):** Another individual attempting to use the device

Training and testing datasets were constructed using user-specific touch-stroke samples.

Undersampling was used to balance positive and negative training samples. The experiments evaluated multiple combinations of legitimate and illegitimate users.

### 3. Model Development

A **Random Forest Classifier** was used as the baseline machine learning model.

Three feature-selection approaches were investigated to reduce unnecessary input features and potentially improve authentication performance.

**Method A — Top 10 Feature Selection**

Selected the 10 most important features and retrained the classification model using this reduced feature set.

**Method B — ExtraTrees Selection**

Used an ExtraTreesClassifier to estimate feature importance and retain features meeting the selected importance criterion.

**Method C — Median Threshold Selection**

Selected features with importance scores greater than or equal to the median feature importance.

### 4. Model Evaluation

Authentication performance was measured using **Equal Error Rate (EER)**.

EER is the error rate at the operating point where the False Acceptance Rate (FAR) and False Rejection Rate (FRR) are equal.

- **FAR:** Proportion of unauthorized attempts incorrectly accepted
- **FRR:** Proportion of legitimate attempts incorrectly rejected
- **EER:** A summary measure of the authentication system's trade-off between FAR and FRR

Lower EER values indicate better authentication performance.

Paired t-tests were also used to compare the feature-selection methods with the baseline model.

## Experimental Results

| Method | Average EER (%) | p-value |
|---|---:|---:|
| Baseline Random Forest | 9.222 | — |
| **Top 10 Selection** | **8.876** | 4.386 × 10⁻⁷ |
| ExtraTrees Selection | 8.889 | 9.729 × 10⁻⁵ |
| Median Threshold | 8.916 | 6.709 × 10⁻⁹ |

### Key Findings

1. All three feature-selection methods achieved lower average EER values than the baseline Random Forest model.
2. Top 10 Feature Selection achieved the best average EER of **8.876%**.
3. Paired t-tests showed statistically significant differences from the baseline for all three methods (p < 0.05).
4. The results suggest that reducing less informative features can improve authentication performance.

The best method achieved an absolute EER reduction of approximately **0.346 percentage points**, equivalent to a **3.75% relative reduction** compared with the baseline.

## Repository Contents

**`data.ipynb`** — Research notebook containing experimental Python code for:

- Touch-stroke data preprocessing and normalization
- Training and testing dataset construction
- Random Forest classification
- Feature-selection experiments
- FAR, FRR, and EER calculations
- Paired statistical tests
- Comparative results visualization

The notebook documents the experimental development and evaluation process.

## Running the Research Notebook

The research code uses Python and Jupyter Notebook, along with several scientific computing libraries.

Install the primary dependencies:

`pip install numpy pandas scikit-learn scipy matplotlib seaborn notebook`

Then open the notebook:

`jupyter notebook data.ipynb`

**Note:** The notebook is an exploratory research implementation and references external CSV datasets and intermediate result files that are not currently included in this repository. The original data files are required to reproduce the experiments. Some notebook cells represent alternative experimental configurations rather than a single sequential execution pipeline.

## Limitations and Future Work

Although the feature-selection methods improved average EER, further research is needed before the approach could be considered suitable for real-world authentication systems.

Potential future improvements include:

- Comparing Random Forest with other classification algorithms
- Investigating additional feature-selection approaches
- Evaluating performance on larger and more diverse user datasets
- Measuring computational efficiency and inference time
- Refining the evaluation protocol for unseen users and touch sessions
- Exploring real-time continuous authentication on mobile devices

## Research Experience

This project provided practical experience in:

- Building and evaluating machine learning classification models
- Processing and analyzing behavioral biometric data
- Addressing class imbalance
- Exploring feature importance and dimensionality reduction
- Designing comparative experiments
- Performing statistical hypothesis testing
- Visualizing and interpreting experimental results
