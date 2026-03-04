Brief Description:
- SHAP is a model explainability framework that explains why a model made a specific prediction by showing the contribution of each feature to the final output.

Overview:
- Machine learning models are often considered black boxes; they produce predictions without explaining why. SHAP solves this by assigning each feature a value that represents its impact on the prediction, making models transparent and interpretable.

Method:
- LinearExplainer is used for Linear Regression models. It requires scaled data to be passed separately due to pipeline preprocessing.
- TreeExplainer is used for XGBoost and Random Forest models fastest and most accurate for tree based models.
- Waterfall plots were generated per prediction showing each feature's contribution. 
- Original input values were restored after scaling to ensure the chart displays human readable values instead of scaled numbers.

Graph Interpretation (from screenshot):
- For a student with study_hours_per_day=8, focus_score=55, sleep_hours=5, attendance_percentage=80:
- E[f(x)] = 47.534  → average productivity score across all students
- f(x) = 56.359  → this student's predicted productivity score

Features Contribution (from screenshot):
- study_hours_per_day = 8 hours   → +13.64 (biggest positive impact)
- attendance_percentage = 80% → +2.34 (small positive impact)
- focus_score = 55% → -2.79 (negative impact)
- sleep_hours = 5 hours → -4.37 (negative impact)
- gender = Male → +0 (no impact whatsoever)

Summary:
- This student scores above average (56.36 vs average 47.53) mainly because of their high study hours. However the student's productivity is being held back by insufficient sleep (5 hours) and a low focus score (55). Improving sleep and focus could push the student's productivity score significantly higher.
