The task of this project was to identify witch aplicants for loans will manage to repay it back.
For this purpose was available complex data consisting of:
- 7 *.csv* files relationed with 3 different primary keys;
- 232 initial features;
- 32,857,652 total number of records.

Performance metric I used ROC AUC. It will help the business get a better understanding about how this algorithm can be used in production and the deployment options (canary deployment/partial automation/full automation etc).

The data was split in training and test tests. Test set was used only once to evaluate final performance of algorithm.
After initial data preprocessing, I have trained various models and tested performance using crossvalidation. Most important results are as follows:
- **First iteration:**
    - Logistic regression: AUC = 0.7459;
    - LGBM: AUC = 0.7550;
    - MLP: AUC = 0.7465;
    - Other models (KNN, Decision Tree, Random Forest, XGB) scored lower results.
- **Feature engineering** with featuretools which resulted in 1759 features:
    - LGBM: AUC = 0.7739;
- **Dimensionality reduction** with PCA: reduce number from 1759 to 336 while keeping 0.99 variation:
    - LGBM: AUC = 0.7499;
- **Feature selection** by dropping least important features. Score on 145 features:
    - LGBM: AUC = 0.7748;
- **Hyperparameter tunning** on 145 features using *Optuna*:
    - LGBM: AUC = 0.7809;
- **Performance on test data**:
    - LGBM: AUC = 0.7906.

Oportunities for further improvement:
- Try to finetune feature creation with featuretools;
- Weight label classes;
- Try to tune hyperparameters for other algorithms that performed well on initial data: MLP. Logistic regression. Then ensemble them.
