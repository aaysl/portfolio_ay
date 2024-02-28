# Goals
<br>
Data set is the Hr Analytics Job Prediction that can be found on <a href="https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv">Kaggle</a>, uploaded by Faisal Qureshi. <br><br>
The Senior leadership team at Salifort Motors is concerned about the high turnover rate at the company and wishes to address the issue.<br>
A high turnover rate is financially costly for the company as Salifort invests heavily in recruitment, training and upskilling its employees<br><br>
The HR team has gathered some data from the employees and has asked to provide data-driven suggestions to be able to introduce initiatives to help improve employee satisfaction.<br><br>

# Materials
All coding was done in the notebook [`Salifort Motors capstone`](https://github.com/aaysl/portfolio_ay/blob/main/Project%203%20Sailfort%20Employee%20Turnover/Salifort%20Motors%20capstone.ipynb).<br>
PACE strategy was drafted and created in [`Capstone - PACE-strategy-document`](https://github.com/aaysl/portfolio_ay/blob/main/Project%203%20Sailfort%20Employee%20Turnover/Capstone%20-%20PACE-strategy-document.docx)<br>
The Executive Summary for Salifort Motors management can be viewed at the document [`Capstone - Executive Summaries`](https://github.com/aaysl/portfolio_ay/blob/main/Project%203%20Sailfort%20Employee%20Turnover/Capstone%20-%20Executive%20Summaries.pptx) *created with Google Executive Summary Template*

# Summary
*for details on the codes and steps taken, please see the notebook linked above*<br>
*codes were done on Coursera's Jupyter for submission purposes*
## Initial Data exploration
Data was pulled in from a csv provided and converted to a Dataframe with pandas.<br>
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/d7858ad2-6b9d-4b54-a89f-02772afa87cf)
## EDA
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/ef92a2e0-50d9-4b77-bb4b-f21e34c19135)
Used `.info()` to surmise the following information: 
- There are no null entries in the dataset
- There are 14999 entries and 10 features
- Department and salary are object datatypes which require conversion to numerical data types for predicitive modelling
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/eafba531-9c84-40ea-b04b-91e050ada288)
Used `.describe(include='all')` to gather descriptive statistics about the data.
For example *not comprehensive list!*:
- I am able to confirm that the column `left` and `promotion_last_5years` contains only binary data.
- The employees here have a maximum `average_montly_hours` of 310hrs and a minimum of 96hrs. A mean of 201.05hrs with a standard deviation of 49.94hrs
- Employee satisfaction mean is around 0.61 with a standard deviation of 0.25
<br>
Before processing anymore data, adjusted the column names as the format are inconsistent and there are spelling errors

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/f863fecb-3144-4f04-aead-74d267903c30)

Reconfirmed that there were no null values

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/f997dec5-7ae3-4924-8efe-52e7744cbb1b)

And checked for duplicated values

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/a8204af3-240d-450f-9390-bda650258d12)

There were 3008 lines of duplicated data.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/98cb5d31-6814-493a-95f3-70e5abc5401d)
Sorted and took a look at 1st 15 lines of data, and there seems to be duplicates.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/b413f18c-52a3-4847-84c5-6f5259df0c4e)
There was no way to verify the information and so the duplicated rows were dropped and mapped to a new dataframe name

### Understanding the data further
Looking at `tenure` distribution and understanding whats the typical range of years that an employee stays in Salifort

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/c6c2e039-c5fe-4046-b4ef-53b809528e8f)

Distribution of employees that left and retained in the dataset

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/8d2975eb-3ddd-48ed-bc7c-47d1f0b4a531)

Distribution of `satisfaction_level`

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/d49a4b91-9459-4f8b-9094-45d68985d6ec)

There are some employees with a fairly high satisfaction level around 0.8 that has left. 

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/6eadb88d-86c8-46f4-9172-4347c1530ca5)

Those that left seem to leave by the 6 year mark. It does not seem to weigh on the satisfaction_level specifically as well. The data seems a little weirdly distributed to make sense at first glance.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/5b856944-3086-47db-be24-633611522bb8)

Evaluation levels peaks, for employees that left, around the higher-end and around 0.5. Is this related to other factors?

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/9f06c02d-10ae-4ce2-a7f8-8c379433ebe1)

There is 2 general chunks that can be seen of people that left. 1 is high evaluation but low satisfaction, and there is an area with middling satisfaction level and evaluation level.

Why did the people with high evaluation leave have such low satisfaction levels?

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/a3961983-8218-441b-b1e4-445c98fb3602)

The clusters of those that left seem to be around high evaluation and high number of projects, as well as those with lower number of projects and middling evaluations. The Latter group may be those already planning to resign and thus low evaluation and lower number of projects? Or maybe those with poor performance.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/f38a2a9a-3696-4a67-9acc-6b211145ac0c)

Employees that left show 2 clusters again. Having high average_monthly_hours but high evaluation, and a those working normal hours but middling evaluation.

Would now look further into number of projects and average_monthly_hours.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/0b3d56cd-aba2-4ab3-a540-67bd3a51e35d)

Seems that the proportion of people who left are higher with 2, 6 or 7 projects.

In the group of 6 & 7 projects, could they also be working longer hours?

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/42f6314d-5d2a-4189-b80f-a740074b4d4c)

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/3f26679c-8429-41d7-8835-f138eab47c2c)

The average work hours are on the high end in this company. Considering a typical 8.5hr work day and a 5 day work week, that would amount to about 170 hrs a month.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/a01afe46-2bbb-4254-97db-1b40f92517c7)

The `average_monthly_hours` worked here is significantly different from assumed standard hours!

To answer the previous question if employees with more projects tend to work more hours.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/f8eb0d11-ba2b-41aa-80e4-aebe0781a740)

Yes. There also seems to be an occurance of when there are high number of projects and long hours, more likely an employee would leave.

How does the company promote its staff? Is there a reason for the long hours & proj numbers leading to turnover?

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/1ceda9cf-1225-42c7-92b0-d54e54fd974c)

Most that did not get a promotion and worked the most hours left. Seems that staff were not properly compensated.

Work accident and department distributions did not show any relation to whether an employee left.
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/8a20119f-610e-45de-ab24-defc85927f38) 
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/068731a4-97cd-44ef-a22b-f8c997ed0570)

These 2 features do not seem to strongly influence in an employee's decision to leave.

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/8c763056-602c-4d86-b9bc-1503d19ce705)

Salary level seems to have an equal distribution of employees leaving. 

### Data Cleaning

Convert `department` and `salary` to numerical values

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/5280284d-ea14-4113-8baa-58fc6c54faa9)

Remove outliers from tenure by capping any values above upper limit

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/aa08edfd-8556-4e01-984e-dc3a022b629f)

### Data Correlation
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/d45cc234-666d-4409-bf97-faaa9f018701)

The 2 features that seem to have some correlation (although not strong) is `average_monthly_hours` and `number_project`

## Modelling
Data was split 30% to test and 70% to train
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/6f3fd81c-0dca-459d-b0a8-6d047d378e8e)

Created a function to calculate and compile metrics from each model
![image](https://github.com/aaysl/portfolio_ay/assets/149126592/aa1b60b9-a1dc-46c3-8bf6-8f47102c01e5)

What do the metrics measure?

|Metrics|Explanation|
|:---:|:---|
|CVS|Evaluates by spliting the data into *k* sets and cross validates the accuracy score across the *k* sets|
|Accuracy|Proportion of correctly identified data points, Balanced formula was used as the data is imbalanced|
|Recall|Proportion of correctly identified Positive data points out of all predicted Positive data points |
|Precision|Proportion of correctly identified Positive data point out of all actually Positive data points|
|f1|Harmonic aggregation of Recall and Precision scoring|


Tested 5 models
- Logistic Regression
- Gaussian Naive Bayes
- Random Forest (with GridSearchCV)
- XGBoost (with GridSearchCV)
- SVM

Here's the compiled metrics

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/fe83764e-4fca-4d0e-ba4a-5d88170a100c)

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/5b81d312-2c0e-4f69-b8db-ab3b721883fa)

XGBoost scored the best across the board on all the metrics measured.

What were the features identified as important in the classification?

![image](https://github.com/aaysl/portfolio_ay/assets/149126592/f46e2ed4-91a9-44e5-84b3-0f8a4a942cfa)

Findings are as follows
- XGB was the best model out of 5 tested
- The top 5 features that influences an employee's continued employment are
    - average_monthly_hours
    - satisfaction_level
    - last_evaluation
    - number_project
    - tenure
- There is a need to ensure that the `average_monthly_hours` worked is closer to standard average. Is there a manpower issue? Are deadlines not set with proper consideration? Or is there a work culture that needs to be adjusted. Promote a better work-life-balance.
- Employees who are assigned a large number of projects (6 and above) are more likely to leave, ensure that there is a maximum number of projects that an employee is assigned to.
- Proper recognition of employees' efforts through promotion should be done.
- More data can be collected, such as specific manager names, staff seniority, staff experience, amount of overtime done, average daily hours and weekly hours
- The model can also be improved by introducing new data and/or looking at different models that can give a more detailed breakdown on how the features influences the employee's decision to leave
<br><br>


That's the end of the project, please contact me if you have any further questions!










