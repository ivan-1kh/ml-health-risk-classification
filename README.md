**Predicting Health Outcomes from Coffee Consumption and Lifestyle
Factors**

**1. Introduction**

This project develops a system to predict health issue severity
(None/Mild/Moderate/Severe) based on coffee consumption and lifestyle
factors. Using a dataset of 10,000 individuals with 16 features
including demographics, coffee intake, sleep patterns, BMI, and
lifestyle choices, we aim to understand the relationship between habits
and health implications.

**Research Questions:**

- Can ML models accurately predict health issues from lifestyle
  patterns?

- What is coffee\'s role relative to other factors?

- Which algorithms perform best for this multi-class problem?

**2. Data Analysis and Feature Engineering**

**a. Data Analysis**

Correlations identified:

- Negative correlation between sleep and coffee intake (-0.42)

- Positive correlation between age and BMI (0.38)

- Inverse relationship between physical activity and BMI (-0.45)

**b. Feature Engineering
([dataset](https://www.kaggle.com/datasets/uom190346a/global-coffee-health-dataset))**

1.  **Coffee_Category**: Low/Medium/High consumption bins

2.  **Age_Group**: Young/Middle/Senior/Elderly categories

3.  **BMI_Category**: WHO (World Health Organization) classification

4.  **Sleep_Deficit**: Binary value (\<7 hours or \>=7 hours)

5.  **Lifestyle_Risk_Score**: Composite of smoking+alcohol+low physical
    activity

6.  **Coffee_Sleep_Ratio**: Interaction feature

7.  **Health_Indicator**: Normalized BMI+heart rate

**c. Preprocessing**

- Label encoding for 8 categorical variables

- StandardScaler normalization

- 80-20 stratified train-test split

- Final feature set: 21 features

Initial analysis revealed health severity correlates most with **sleep
patterns**, **age-BMI combinations**, and **lifestyle factors**, while
coffee alone showed weak direct correlation.

**3. Methodology**

**a. Algorithms**

**Decision Tree**

- Parameters: max_depth=5, min_samples_split=20

- Purpose: Understandable rules and feature importance

**Random Forest (Ensemble)**

- Parameters: n_estimators=100, max_depth=10

- Purpose: Reduce overfitting through bootstrap aggregation

**AdaBoost (Boosting)**

- Parameters: n_estimators=100, learning_rate=0.8

- Purpose: Adaptive learning focusing on misclassified instances

**b. Evaluation Strategy**

Models were evaluated using **accuracy**, **precision**, **recall**,
**F1-score**, and **ROC-AUC**.

5-fold cross-validation ensured good performance estimates.

GridSearchCV optimized Random Forest hyperparameters.

**4. Results**

**a. Model Performance**

| **Model**     | **Accuracy** | **Precision** | **Recall** | **F1-Score** | **CV Score**       |
|---------------|--------------|---------------|------------|--------------|--------------------|
| Decision Tree | 99.35%       | 99.0%         | 99.0%      | 99.0%        | 99.56% ± 0.26%     |
| **AdaBoost**  | **99.45%**   | **99.0%**     | **99.0%**  | **99.0%**    | **99.74% ± 0.20%** |
| Random Forest | 99.25%       | 99.0%         | 99.0%      | 99.0%        | 99.36% ± 0.15%     |

**b. Feature Importance (Top 5)**

1.  **Sleep_Hours** (0.220) - Primary health predictor across all models

2.  **Age** (0.195) - Strong correlation with health severity

3.  **Stress_Level** (0.160) - Encoded stress categories highly
    predictive

4.  **BMI** (0.142) - Key physical health indicator

5.  **Lifestyle_Risk_Score** (0.095) - Composite lifestyle factor

Main takeaway: Coffee_Intake ranked much lower (importance: 0.016).

**c. ROC-AUC Analysis**

Multi-class discrimination showed excellent performance:

- None: 0.91 \| Mild: 0.84 \| Moderate: 0.86 \| Severe: 0.89

Models best identified healthy individuals and severe cases, with
slightly lower performance on intermediate categories.

**5. Conclusions**

We successfully developed ML models achieving 99%+ accuracy in
predicting health issues from lifestyle factors. The analysis shows that
coffee affects health indirectly through sleep disruption rather than
directly on the body. Random Forest is the optimal model, balancing
accuracy with clarity.

**Practical Implications:**

- Prioritize sleep (≥7 hours) regardless of coffee intake

- Focus on regular physical activity (\>5 hours/week)

- Address multiple lifestyle factors rather than single habits

- Implement age-appropriate BMI monitoring

**Limitations:**

- Synthetic data may not capture all real-world complexity

- Missing confounders (genetics, medical history)
