# HR Analytics – Predict Employee Attrition

Understand why employees leave and predict who's likely to leave next, using EDA, classification models, and an interactive Power BI dashboard.

## Objective

Use analytics to understand the main causes of employee resignation and predict future attrition, so HR can act before an employee leaves rather than after.

## Dataset

[IBM HR Analytics Employee Attrition Dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) (Kaggle) 1,470 employee records, 16.1% overall attrition rate.

## Tools

- **Python** — Pandas, Seaborn, Matplotlib, scikit-learn
- **Power BI** — interactive dashboard
- **Jupyter Notebook** — EDA and modeling

## Repository Structure

| File / Folder | Description |
|---|---|
| `HR_Analytics_Predict_Employee_Attrition/` | Notebook, cleaned data exports, and all generated chart images |
| `HR_Analytics_Predict_Employee_Attrition/Analytics.ipynb` | Full analysis: EDA, model training, evaluation, feature importance |
| `HR_Analytics_Predict_Employee_Attrition/WA_Fn-UseC_-HR-Employee-Attrition.csv` | Raw source dataset |
| `HR_Analytics_Predict_Employee_Attrition/hr_attrition_cleaned_for_powerbi.csv` | Cleaned dataset used to build the Power BI dashboard |
| `HR_Analytics_Predict_Employee_Attrition/feature_importance.csv` / `.png` | Decision Tree feature importance rankings |
| `HR_Analytics_Predict_Employee_Attrition/confusion_matrix_logreg.png`, `confusion_matrix_tree.png` | Model evaluation visuals |
| `HR_Analytics_Predict_Employee_Attrition/chart_*.png` | EDA charts (attrition by department, overtime, income, tenure, job satisfaction, correlation heatmap) |
| `IBM HR Analytics Dataset/` | Original dataset folder |
| `HR_Analytics_Attrition.pbix` | Power BI dashboard file |
| `HR_Analytics_Dashboard.png` | Dashboard screenshot |
| `HR_Attrition_Prevention_Reporting.pptx` | Findings, model comparison, and HR prevention recommendations (slide deck) |

## Approach

1. **EDA** — explored attrition patterns by department, salary, overtime, tenure, and job satisfaction
2. **Modeling** — trained and compared two classifiers:
   - Logistic Regression (baseline, interpretable)
   - Decision Tree (max depth 5)
3. **Evaluation** — accuracy, precision, recall, F1, and confusion matrices on a stratified 80/20 train-test split (1,176 train / 294 test)
4. **Explainability** — feature importance from the Decision Tree to identify the top drivers of attrition
5. **Visualization** — Power BI dashboard for interactive exploration
6. **Recommendations** — translated top drivers into concrete HR prevention actions

## Key Results

| Metric | Logistic Regression | Decision Tree |
|---|---|---|
| Accuracy | 0.690 | 0.765 |
| Precision (Attrition) | 0.307 | 0.351 |
| Recall (Attrition) | **0.745** | 0.553 |
| F1 Score (Attrition) | 0.435 | 0.430 |

**Recommended model: Logistic Regression** despite lower overall accuracy, it catches far more employees who actually leave (74.5% recall vs. 55.3%), which matters more than raw accuracy in an attrition-prevention setting where missing an at-risk employee is costlier than a false alarm.

### Key Insights from the Dashboard

- **1,470** employees analyzed, **237** attritions (**16.1%** attrition rate)
- Average employee age: **36.9** years; average monthly income: **$6.5K**
- **Overtime employees leave far more often** 127 attritions among those working overtime vs. 110 among those who aren't, despite overtime being the minority group overall
- **Gender split of leavers**: 150 male vs. 87 female
- **Marital status of leavers**: Single employees make up the largest share (120, 50.6%), followed by Married (84, 35.4%) and Divorced (33, 13.9%) single employees are markedly more likely to leave
- **Highest-attrition job roles**: Sales Representative (39.8%), Laboratory Technician (23.9%), Human Resources (23.1%), Sales Executive (17.5%), Research Scientist (16.1%)
- **Job satisfaction**: level-1 (lowest satisfaction) employees account for a disproportionate share of attrition relative to their group size, alongside level-3 employees (30.8% of attritions)  satisfaction alone doesn't cleanly predict leaving, reinforcing why workload and tenure-based factors (overtime, working years) matter more in the model

### Top drivers of attrition (Decision Tree feature importance)

1. Total Working Years
2. OverTime
3. Age
4. Stock Option Level
5. Num. Companies Worked
6. Monthly Income

Full context, charts, and HR prevention recommendations for each driver are in `HR_Attrition_Prevention_Reporting.pptx`.
