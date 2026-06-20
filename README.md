Pima Diabetes - ML Classification Comparison

Comparing 7 supervised learning models on the Pima Indians Diabetes 
dataset to predict diabetes onset. Focuses on handling class imbalance, 
fixing overfitting, and evaluating models beyond accuracy.

 Dataset:-
  Source: Pima Indians Diabetes Database (UCI / Kaggle)
  Rows: 768 patients, Features:8, Target:Diabetic (1) or Not (0)
  Class Imbalance: 65% Non-Diabetic / 35% Diabetic
  Key Challenge: 5 columns had biologically impossible zero values 
  (Glucose, BloodPressure, SkinThickness, Insulin, BMI) — 
  treated as missing and filled with median imputation

Preprocessing Steps
1. Replaced `0` values in 5 columns with `NaN`
2. Filled missing values with column median
3. Stratified train-test split (80/20)
4. StandardScaler normalization
5. 'class_weight='balanced' on all models to handle class imbalance

Results

| Model | Train Acc | Test Acc | Gap | Precision | Recall | F1 Score |
| Logistic Regression | 75.7% | 70.1% | 5.6%  | 56.5% | 70.9% | 62.9% |
| Decision Tree | 78.5% | 70.1% | 8.4% | 59.6% | 61.8% | 60.7% |
| SVM (RBF kernel) | 81.4% | 73.4% | 8.0%  | 59.7% | 78.2% | 67.7% |
| Random Forest | 84.4% | 74.7% | 9.7% | 60.5% | 83.6% | 70.2% |
| KNN (K=12) | 78.8% | 72.7% | 6.1% | 64.3% | 50.0% | 56.3% |
| XGBoost | 89.0% | 74.0% | 5.0% | 60.6% | 78.2% | 68.3% |
| Naive Bayes | 76.4% | 70.1% | 6.3% | 56.7% | 63.0% | 59.7% |

 Key Findings

Random Forest achieved the best F1 score (70.2%) and highest test accuracy (74.7%)
Decision Tree without depth restriction overfit severely (Train 100%, Test 70.1%, Gap 29%)  fixed with 'max_depth=4' and min_samples_leaf=10
Random Forest also overfit initially (Train 100%) fixed with max_depth=6 and min_samples_leaf=5
Recall prioritized over Precision in medical diagnosis, missing a diabetic patient is more costly than a false alarm
Accuracy alone is misleading with class imbalance F1 score used as primary evaluation metric

Skills Demonstrated

Missing value detection and imputation
Class imbalance handling
Overfitting diagnosis and fixing
Model comparison using multiple metrics
Supervised learning: LR, DT, RF, SVM
