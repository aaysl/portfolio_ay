# Goals
<br>
Dataset was provided by NTUC Learning Hub as part of the SCTP Data Analyst Course Capstone Project<br>
Additionally, this resembles the <a href=https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset>Cardiovascular Disease dataset</a>  on kaggle.
<br><br>
With the sample dataset from Parkway Pantai, create a predictive model that can accurately classify individuals as either <b>having</b> or <b>not having</b> heart disease.<br><br>

# Notebooks
In [`P1-1 EDA.ipynb`](https://raw.githubusercontent.com/aaysl/portfolio_ay/main/Project%201%20CVD%20Prediction/P1-1%20EDA.ipynb), data set was analysed and cleaned using Python.
<br><br>
In [`P1-2 Modelling.ipynb`](https://raw.githubusercontent.com/aaysl/portfolio_ay/main/Project%201%20CVD%20Prediction/P1-2%20Modelling.ipynb), using the cleaned dataset, relationship analysis was done with the different features of the dataset. Comparing different machine learning algorithms, the best was selected to make a prediction based on a test subset.

# Summary
*for details on the codes and steps taken, please see the notebooks linked above*<br>
*Cardiovascular disease will be referred to by the abbreviation CVD*
## Initial Data exploration
Data was pulled in from Postgresql and converted to a Dataframe with pandas.<br><br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/4411c112-b23e-4219-acb8-4ef5847cfb28)<br><br>
Took a cusory glance at the data to understand what was being worked with (such as what data types, nulls, duplicates, no of unique entries), <br>
and came to the following conclusions.<br><br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/3ceee1ff-8a0f-4322-ad0b-b1d277690181)<br><br>
## Data Cleaning and exploration
Took the following steps to clean the data
- Converted age column to years
  - Checked on the data distribution
- Check data entries in active, smoke, disease, cholesterol and gluc
  - What are the unique entries and what they represented
  - Data distribution
- Checked on weight and height
  - Both weight and height have a large data range which is not representative of a normal population
  - Calculated bmi and cleaned up outliers based on weight and height
  - Dropped weight and height columns
  - Checked distribution of bmi data
-  Checked on ap_hi and ap_lo
  -  Converted negative values to positive
  -  Removed any data outside of feasible range
  -  Checked for instances of ap_hi<ap_lo and removed accordingly
  -  Checked distribution of both ap_hi and ap_lo data
- Converted country column to numerical categoricals with `.get_dummies()`
- Dropped occupation column and date column as it was not required for analysis
- Ensured all floats (except BMI) was converted to smallint for smaller memory usage
- Uploaded cleaned data to Postgresql as new table.<br><br>
Result of cleaning:<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/4f7761f9-3ad6-45ca-ae3f-b3f0256baeb4)<br><br>
## Understanding the Data
Using the cleaned data
- Looked at the distribution of data by age and disease presence
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/980916d5-e580-4d8f-8b40-16fa43e75972)
- Looked at distribution of data (bmi, age, ap_hi and ap_lo) and disease presence by histogram plots
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/0ab8de79-9e4f-4d02-983d-607523ba65ff)
- Distribution of data (active, alco, smoke, gluc and cholesterol) and disease presence by violinplots
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/e9b7c57c-839d-4a46-81da-f2419eedd5ef)
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/37a52e02-ba53-4977-941c-c4610611dee1)
- Learnt that the data is skewed to a small age range, most entries do not smoke, drink alcohol and are active
- The data is also mostly comprimised of individuals with healthy levels of glucose and cholesterol
## Looking at Correlation
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/6572a908-33fe-4e18-b570-efd61c4aee66)
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/cb4bcad4-ce5f-405c-8a3b-6edf0fdec323)
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/47f850a5-6637-45c5-8b57-ea8647bc05ac)
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/5b336063-44e7-4abe-a58a-98f36a4576c3)
## Split Data
Using `train_test_split()` from scikit-learn, we split the data into 2 datasets.<br>
1 is the train data set, which comprimises 80% of the data, and will be used to train the machine learning models.<br>
The other is the test data set, which comprimises the other 20% of the data (not the same data as train data set!), and will be used to test the models.<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/4e333e0f-2b84-40e4-bcc8-8927184cb390)
## Training and Testing the models
Will be using the following ML algorithms/models
- Logistical Regression
- k-Nearest Neighbor
- Support Vector Matrix
- Decision Tree Classification
- Random Forest
- Gaussian Naive Bayes
For each model will be obtaining the following accuracy scores:
- Cross validation score with `cross_val_score()`
- Balanced accuracy score with 'balanced_accuracy_score()`
- f1 score with `f1_score`
And displaying the confusion matrix to give a feel of the number of false positives and false negatives obtained.<br>
All the calculations were created in a functions for ease of application to all models.<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/aaae1d94-1e1f-4604-9261-1ad8fe9705e9)<br><br>
A sample of the output can be seen here:<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/ad9cd1aa-875d-4865-8077-ae1f2dc04075)<br><br>
An evaluation of the models can be done by plotting their accuracy scores<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/ccdfa25f-23bb-4e27-8c09-31b67a2e2d2e)<br><br>
A simple function can be built to give a statement style prediction:<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/9bd98c7a-3b54-46e0-9bce-5d5334366a69)<br><br>

That's the end of the project, please contact me if you have any further questions!










