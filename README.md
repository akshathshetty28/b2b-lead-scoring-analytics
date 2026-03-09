# b2b-lead-scoring-analytics
## Project Overview:
This project aims to predict whether a customer will convert based on historical behavioral and demographic data.

The goal is to help marketing teams:
- Identify high-profitability converters.
- Optimize outreach strategy.
- Reduce wasted campaign spending.

## Problem Statement 
The dataset is highly imbalanced, with only ~11% positive conversions.

Using accuracy alone is misleading because a model can achieve 89% accuracy by predicting all customers as non-converters.

Therefore, the focus of this project is:
- Improving recall
- Balncing Precision-Recall trade-offs
- Optimizing decision thresholds based on business objectives.

## Technology Used:
- Python
- Pandas/Numpy
- Scikit-learn
- Matplotlib
- Random Forest
- Logisitc Regression

## Modeling Approach:
1. Baseline Model - Logisitic Regression
   - Trained using default threshold(0.5)
   - Observed high accuracy but poor recall due to class imbalance

2. Random Forest Model
   - Improved performance over baseline
   - Captured non-linear relationships
   - Still suffered from low recall at default threshold.

3. Threshold Tuning (Key Contribution)
   Instead of using the default 0.5 threshold, proability outputs were analysed using:
   - ROC curve
   - Precision-Recall Curve
   - F1 Score Optimization
   - F2 Score Optimization (recall-focused)
  
## Results
### Default Threshold (0.28)
- High Accuracy (~90%)
- Low recall
- Many converters missed

### F1-Optimized Threshold (0.28)
| Metric              | Value     |
| ------------------- | --------- |
| Precision           | 0.54      | 
| Recall              | 0.71      | 
| F1 Score            | 0.615     |  


Provides a balanced tradeoff between precision and recall

### F2 - Optimized Threshold (0.18)
| Metric              | Value     |
| ------------------- | --------- |
| Precision           | 0.45      | 
| Recall              | 0.85      | 
| F2 Score            | 0.724     | 


Captures 85% of converters - ideal for growth-focused marketing strategies.

## Business Interpretation:
- If marketing budget is limited -> use threshold 0.28
- If maximising conversions is priority -> use threshold 0.18

This project demonstrates how threshold tuning significantly improves model effectiveness in imbalanced classification problems.

| Model               | Threshold | Precision | Recall | F1    |
| ------------------- | --------- | --------- | ------ | ----- |
| Logistic Regression | 0.5       | ...       | ...    | ...   |
| Random Forest       | 0.5       | ...       | ...    | ...   |
| Random Forest       | 0.28      | 0.54      | 0.71   | 0.615 |
| Random Forest       | 0.18      | 0.45      | 0.85   | 0.724 |

## Key Learnings
- Accuracy is misleading for imbalanced datasets.
- Threshold tuning is critical in real-world ML applications.
- Business context should guide metric selection.
- F1 vs F2 score selection depends on objective.

## Future Improvements
- Hyperparameter tuning with GridSearchCV
- Feature importance analysis
- SHAP for model interpretability
- Deploy model using Flask/Streamlit
- Cost-sensitive learning

## Marketing Campaign Targeting Simulation
To evaluate the real-world impact of the model, a campaign targeting simulation was conducted.

Instead of contacting every customer, the model was used to rank customers by their predicted probability of subscribing to a term deposit. The bank can then focus its outreach on customers with the highest predicted likelihood of conversion.

### Baseline Strategy
If the bank contacts all customers:
- Conversion rate: 27.4%

### Model-Based Targeting Strategy
If the bank contacts only the top 30% of customers ranked by predicted probability:
- Conversion rate: 27.4%

### Business Impact
This represents a 2.3x improvement in campaign efficiency.

In practical terms:
- Without the model: contacting 1000 customers results in approximately 117 subscriptions.
- With model-based targeting: contacting 300 high-probability customers results in approximately 82 subscriptions.

This means the bank can achieve nearly the same number of conversions while making 70% fewer calls, significantly reducing campaign costs and improving marketing efficiency.

## Key Insight:
Machine learning can help financial institutions prioritize high-value customers, enabling more efficient marketing campaigns and better allocation of call center resources.


