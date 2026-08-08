Building Risk Models to Predict Railroad Accident Severity 
Tanner Hilt - Capstone Project

Project Description
The purpose of this project is to investigates whether pre-incident features from the FRA Form 6180.54 dataset can help railroad industry professionals determine the severity of accidents/incidents involving their equipment. Feature engineering risk score and risk category as the two target variables for a regression and classification model.
Research Question: Is it possible to develop a risk model that helps professionals in the railroad industry determine the severity of an accident/ incident involving equipment?
Hypothesis: Pre-incident features from the FRA Form 6180.54 data source provide enough information to establish risk scores and classifications for railroad accidents more effectively than a dummy model.
Repository Structure
[Capstone Folder]
| - Data # Raw Data, Data Dictionary, and Cleaned Data Sets
            | - cleaned_FRA_data_no_targets # Cleaned Data Set
            | - Raw Data and Dictionary 
	          | - FRA Raw Date # Raw Dataset/ Used for FRA Reproduce Document
	          | - FRA (Form 54) Column Dictionary # Feature Dictionary
| - Notebook Documents # Jupyter Notebooks
           | - 0) Capstone PostgreSQL Import Document # Connecting Raw Data to Database
           | - 1) Capstone Reproduce Document # Document for Reproducibility
           | - 2) Capstone Master Document # Personal Document/ Containing SQL EDA
| - Presentation Documents # 
           | - Capstone Final Presentation 
           | - Capstone Final Report
Data Source
Data was pulled from the Federal Railroad Administration (FRA) Form 6180.54 via the publicly available U.S. Department of Transportation’s site: https://data.transportation.gov/Railroads/Rail-Equipment-Accident-Incident-Data-Form-54-/85tf-25kj
The original dataset contained 224,700 records with 155 features, spanning from 1975 to 2026. Database used was PostgreSQL and pulled into a Jupyter Notebook. After data cleaning, the remaining records explored were 159,995 with 26 features.
Note: Data was having technical difficulties in reproducibility via using a CSV file versus a PostgreSQL pull. Corrections were made. Capstone Master Document was added to showcase EDA via SQL and to validate results if an error occurs.
How to Run
1)	Download the Capstone Reproduce Document located in Notebook Document
2)	Download data titled FRA Raw Data located in Data – Raw Data and Dictionary
3)	Change pd.read_csv connection to data location on personal device
a.	All packages needed are in the notebook
4)	Run notebook – Takes roughly 10 minutes
Library Overview
•	Pandas: pandas - Python Data Analysis Library
•	NumPy: NumPy
•	Scikit-learn: scikit-learn: machine learning in Python — scikit-learn 1.9.0 documentation
•	XGBoost: https://xgboost.readthedocs.io/en/stable/python/python_api.html
•	SciPy: SciPy
•	Matplotlib: Matplotlib — Visualization with Python
•	Seaborn: seaborn: statistical data visualization — seaborn 0.13.2 documentation
Methodology 
•	Data Split: Chronological - train (1975-1997)/ validation (1998-2011)/ test (2012-2026. 
•	Cross-validation: TimeSeriesSplit with 5 folds. 
•	Models: XGBoost Regressor and Classifier for final evaluation. DummyRegressor and DummyClassifier for baseline model. Linear Regression and KNN for exploration.
•	Tuning: GridSearchSV – scoring via negative RMSE and F1-macro
•	Statistical Tests: Paired t-test and bootstrap resample (5 Folds)
Results
•	Regression Test: R-squared at 0.293 and RMSE at 0.934
•	Regression Dummy: R-squared -0.002
•	Classification Test: F1-macro at 0.61
•	Classification Dummy: F1-macro at 0.503
•	Models are statistically significant (p-value < 0.05 and 95% CI contain no 0 value)
Limitations
•	Classification model misses a large number of High Severity Cases
•	Linear Regression and KNN models were not evaluated for statistical testing against the XGBoost model
•	Risk score is expressed in standard normal format, not optimal for non-technical users
Intended Use
This model is intended as a support tool for initial decision-making for mitigation strategy. Not a final decision-maker due to unexplained variance and missing High Severity cases. Additional investigation should be used. 
