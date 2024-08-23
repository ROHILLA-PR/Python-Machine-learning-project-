
# Insurance Applicant Risk Analysis

# Dataset Source
https://www.kaggle.com/datasets/sooyoungher/smoking-drinking-dataset/data

## Problem Statement

Insurance firms evaluate applicants through a process known as underwriting. This process involves assessing the risk associated with insuring an individual and determining the terms of coverage, including premiums and policy limits.

A vital component of this analysis is the health assessment, where applicants are asked about their medical history, lifestyle choices (e.g., smoking, drinking), and current health status. Since a drinking and/or smoking habit could lead to a higher risk score, and consequently a higher premium or application rejection, applicants might hide this information, leading to potential losses for the insurance firms. 

The goal of this project is to accurately classify a person as a smoker or drinker based on common health metrics used by insurance agencies.

## Dataset

This dataset, collected from South Korea’s National Health Insurance Service via Kaggle, consolidates information from 1 million patients. It includes two columns indicating if each patient is an active drinker and/or smoker. There are 20+ variables for each patient, including standard metrics such as sex, age, height, weight, blood pressure readings, cholesterol, triglyceride numbers, and enzyme readings that indicate liver and kidney function.

## Exploratory Data Analysis (EDA)

### Preliminary EDA

- **Gender Distribution:** There's a near equal split of males and females in the dataset.
- **Smoking Insights:** Most smokers in the dataset are males, with nearly 70% of males having smoked at some point in their lives, compared to only ~5% of females.
- **Correlation Between Smoking and Drinking:** A person who smokes (or has at some point) is almost three times as likely to be a drinker. On the contrary, someone who has never smoked is unlikely to drink.
- **Age and Smoking:** Most of the people who have smoked at least once are in their 40s or 50s, and almost half the people in their 30s are smokers.
- **Age and Drinking:** Most drinkers are in their 40s. Taller and heavier individuals are more likely to drink. The percentage of drinkers tends to be higher (>50%) with higher total cholesterol levels (180+). However, the percentage of drinkers decreases in higher age groups (50+).

### Post Feature Engineering

We added several features to the dataset to potentially improve prediction accuracy, including:
- Liver Enzyme Ratio
- Liver Damage Score
- BMI
- HDL:LDL ratio

While some new features showed promise, particularly the liver function features, others did not significantly impact the feature importance lists.

## Solution & Insights

To predict a patient’s drinking and/or smoking habit, we considered six different algorithms for classification:

1. **Logistic Regression**
2. **K-Nearest Neighbors (KNN)**
3. **Naive Bayes**
4. **Decision Tree**
5. **Random Forest**
6. **Bagging**

Each model was tested under five scenarios:
- Predicting drinking status (original dataset)
- Predicting smoking status (original dataset)
- Predicting drinking status (engineered dataset)
- Predicting smoking status (engineered dataset)
- Predicting drinking and/or smoking status (engineered dataset)

### Baseline Performance

- If we assume everyone is a drinker, about 50% of them actually are.
- If we assume everyone isn’t a smoker, about 60% of them actually are.
- If we assume everyone either drinks or smokes, about 60% actually fall into that category.

### Model Performance

**Best Performing Models:**
- **Drinker Prediction:** The Random Forest model (pre-feature engineering) performed best, although it may suffer from overfitting.
- **Smoker Prediction:** The Decision Tree model (with feature engineering) performed best.
- **Smoker and/or Drinker Prediction:** The Random Forest model performed best, with results roughly 20% better than the baseline.

### Insights

- **Age:** Crucial for drinking predictions, but less so for smoking predictions.
- **Liver Damage Indicators:** Liver_damage_score is a key feature in decision trees, random forests, and KNN models. The liver_enzyme_ratio is important in logistic regression, demonstrating that different models utilize the same information differently.
- **Smoking vs. Drinking Predictions:** Smoking predictions are generally more accurate than drinking predictions, likely due to the nearly even split of drinkers and non-drinkers.
