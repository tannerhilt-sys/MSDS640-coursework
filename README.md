Building Risk Models to Predict Railroad Accident Severity 

Tanner Hilt - Capstone Project

Project Description

The purpose of this project is to investigates whether pre-incident features from the FRA Form 6180.54 dataset can help railroad industry professionals determine the severity of accidents/incidents involving their equipment. Feature engineering risk score and risk category as the two target variables for a regression and classification model.

Research Question: Is it possible to develop a risk model that helps professionals in the railroad industry determine the severity of an accident/ incident involving equipment?

Hypothesis: Pre-incident features from the FRA Form 6180.54 data source provide enough information to establish risk scores and classifications for railroad accidents more effectively than a dummy model.


Repository Structure



<img width="747" height="335" alt="image" src="https://github.com/user-attachments/assets/b51d52d5-fd8c-4bf4-8865-318a78de8499" />



   
Data Source

Data was pulled from the Federal Railroad Administration (FRA) Form 6180.54 via the publicly available U.S. Department of Transportation’s site: https://data.transportation.gov/Railroads/Rail-Equipment-Accident-Incident-Data-Form-54-/85tf-25kj

The original dataset contained 224,700 records with 155 features, spanning from 1975 to 2026. Database used was PostgreSQL and pulled into a Jupyter Notebook. After data cleaning, the remaining records explored were 159,995 with 26 features.

Note: Raw dataset was too massive for upload. However, the website is a LIVE dataset that is constantly being updated. After testing new dataset on webpage, current notebook will not run because there is something wrong with the data. Massive limitation! However, I rebuilt the notebook and downloaded the clean dataset version I have so results can be run. There is a small difference in scores.


How to Run
1)	Download the Capstone Reproduce After Cleaning Document located in Notebook Document
2)	Download data titled cleaned_FRA_data_no_targets located in Data – Raw Data and Dictionary
3)	Change pd.read_csv connection to data location on personal device
a.	All packages needed are in the notebook
4)	Run notebook – Takes roughly 10 minutes

   
Library Overview

1) Pandas: [pandas - Python Data Analysis Library](https://pandas.pydata.org/)
2) NumPy: https://numpy.org/
3) Scikit-learn: https://scikit-learn.org/stable/index.html
4) XGBoost: https://xgboost.readthedocs.io/en/stable/python/python_api.html
5) SciPy: https://scipy.org/
6) Matplotlib: [Matplotlib — Visualization with Python](https://matplotlib.org/)
7) Seaborn: seaborn: [statistical data visualization — seaborn 0.13.2 documentation](https://seaborn.pydata.org/)


Methodology 

1) Data Split: Chronological - train (1975-1997)/ validation (1998-2011)/ test (2012-2026)
2) Cross-validation: TimeSeriesSplit with 5 folds
3) Models: XGBoost Regressor and Classifier for final evaluation. DummyRegressor and DummyClassifier for baseline model. Linear Regression and KNN for exploration.
4) Tuning: GridSearchSV – scoring via negative RMSE and F1-macro
5) Statistical Tests: Paired t-test and bootstrap resample (5 Folds)


Results

1) Regression Test: R-squared at 0.293 and RMSE at 0.934
2) Regression Dummy: R-squared -0.002
3) Classification Test: F1-macro at 0.61
4) Classification Dummy: F1-macro at 0.503
5) Models are statistically significant (p-value < 0.05 and 95% CI contain no 0 value)


Limitations

1) Classification model misses a large number of High Severity Cases
2) Linear Regression and KNN models were not evaluated for statistical testing against the XGBoost model
3) Risk score is expressed in standard normal format, not optimal for non-technical users


Intended Use

This model is intended as a support tool for initial decision-making for mitigation strategy. Not a final decision-maker due to unexplained variance and missing High Severity cases. Additional investigation should be used. 
