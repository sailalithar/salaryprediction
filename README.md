# Predicting Salary Based on Job Description
## Introduction

For this project I have worked on predicting salaries of employees based on the job profile. In any industry we will have the job description with requirements as the job type company needs to fill, the minimum degree they are considering with any preferred major,  years of experience they are looking for and how far is the job from the nearest big city. With the above details I have implemented to estimate the salary for that position. 

This helps both the employers and the employee to get an idea of the salary range and proceed accordingly. Instead of taking industry average salary for the job if we can predict better this helps both HR persons and managers to provide a good salary range. 

## Data Collection

All the data that is used for this project is taken from a kaggle competition. The 9 features collected are: jobId, companyId, jobType, degree, major, industry, yearsExperience, milesFromMetropolis and salary. There are 63 companies with 8 job types in 7 different industries. A total of 1000000 salaries are extracted.

## Preprocessing

As part of data cleaning, I implemented the following steps:
  1. Checked for the correctness of datatypes of columns
  2. Removed any duplicate data
  3. Cleaned all NaN values
  4. Dropped invalid data with salary<0 (5 rows in total)
The final count of rows in training set is now down by 5.

## Exploratory Data Analysis

Before building predictive models, I performed exploratory data analysis to see any correlation between the features and also to salary. The minimum salary is 17 and maximum is 301 with 50% around 114. 

![image](https://user-images.githubusercontent.com/22568418/110972162-b0521800-8329-11eb-9568-c3638eaa23e9.png)

As the above heatmap shows, yearsExperience has positive correlation whereas milesFromMetropolis has negative correlation with salary.

![image](https://user-images.githubusercontent.com/22568418/110972417-fa3afe00-8329-11eb-9cd1-d1aa19be63d6.png)

Also from the boxplot it shows clearly that CTO, CFO and CEO salaries are much higher than Janitors.

![image](https://user-images.githubusercontent.com/22568418/110972783-6158b280-832a-11eb-8997-6453cafdc1b1.png)

Similary I could see positive correlation between features jobType, degree, major, industry, yearsExperience to salary. Whereas milesFromMetropolis shows negative correlation to salary. Features jobId and companyId are not influencing salary so they can be neglected.

# Modeling

Industry average of salaries is taken as baseline model and mean squared error is calculated to see the efficiency. It gave around 1367 value for MSE.

Then 3 different models are implemented on the dataset to predict the salaries. Based on the EDA, removed jobId, companyId columns from dataset and also scaled yearsExperience, milesFromMetropolis columns. All other categorical variables are changed to numeric values.

The dataset is split into training data and test data with 70% and 30% respectively. Then models are implemented and efficiency is measured with mean square error using 5 fold cross validation.

![image](https://user-images.githubusercontent.com/22568418/110974196-4424e380-832c-11eb-8576-a92959ac1fde.png)

Gradient boosting tree clearly provided the best results. This is used to predict the salaries on 30% data divided for testing. Below is the distribution plot which shows how the model performed by comparing actual values to predicted values.

![image](https://user-images.githubusercontent.com/22568418/110977987-ce6f4680-8330-11eb-91af-9cf6f1d4f8bb.png)

# Conclusion

The gradient boosting model took jobtype_janitor, yearsExperience and milesFromMetropolis as important features in determining salaries based on job profile. This can be used by HR/Managers to predict salaries that can be offered to the job description.
