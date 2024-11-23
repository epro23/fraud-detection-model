# fraud-detection-model
## Project Scope

The purpose of this project is a simple proof of knowledge of key data analysis/science skills learned through Google's advanced data analytics course and independent self guided studying. This will be accomplished by analyzing a synthetic dataset of credit card transactions sourced from Kaggle and creating a machine learning model to predict fraudulent transactions.

Dataset link: https://www.kaggle.com/datasets/bhadramohit/credit-card-fraud-detection

## Milestone Goals

Look to incorporate the PACE framework plan, similar to the scientific method;

1. Plan:
    * Research relevant information; what constitutes credit card fraud? How is it commonly detected?
    * Familiarize myself with dataset. Clean data. Are there extreme outliers? Missing data?
    * Refine project scope, develop workplan.
2. Analyze:
    * Format the dataset. Label encoding? Class balancing? Normal distributions?
    * Visualize and analyze the dataset. Obvious correlations? Consider data homogeneity, feature correlation, etc...
3. Construct:
    * Feature selection, isolate outcome variable and split data to train model.
    * Build the model. Looking to refine random forest modelling skills.
        * Define, fit, and run each optimized model after cross validation. Collect scores.
        * For the sake of computing time and comparison, may consider XGBoost as well.
    * Determine champion model. Complete feature engineering and rerun, if sensible.
    * Collect predictive results.
4. Execute:
   * Generate visuals of model results on testing set.
   * Deliver executable highlighting key findings, potential model revisions, and business solutions.

## Post Completion Comments

See ipynb file for more detailed commentary of project rationale. Conclusion follows;

A successful model was generated to predict credit card fraud with ~91.5% recall and an f1 score of ~95% in a synthetic dataset with uniformly distributed data. This model employs the use of common data science tools like cross validation, one hot encoding, upsampling, and gradient boosting and random forest models among other tools. Feature selection was conducted following the guidance of appropriate visualizations, and various parameter conditions and scoring metrics were tested to handle inconsistencies within the dataset. These included a significant class imbalance in the the target variable and uniform distributions amongst predictor variables.

A critique of the model may be that upsampling was performed after the data split. Testing data was upsampled, lowering its real world value. With the initial 99:1 class imbalance of the target variable, without expending significant computing resources, upsampling was necessary for this model. To maintain a degree of imbalance, the upsampling was conducted up to 80:20. This has the added benefit of simplifying hyperparameter tuning with cross validation. The cross validation and hyperparameter definitions were designed to prevent overfitting, which should help nullify the risk of overfitting from synthetic upsampling by adding elements of randomness. Combined with the use of a third validation split, the model should be quite robust. It is said that a valid model, trained with synthetic data or not, is more beneficial in practice than one with poor performance.

A clear path forward is presented to increase model performance (metrics), outside of expending significant computational power;
* Feature engineering: generate the previously described transaction_frequency and transaction_deviance features
* Balance classes: ideally to a near 50:50 split for maximal performance, and apply further penalizations to false negatives like custom class_weights and refit the model to the recall metric
* Adjust classification thresholds: can directly optimize precision and recall this way to maximize model performance for either metric
