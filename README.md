# Data Science Salary Estimator: Project Overview 
* Created a tool that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
* Used https://www.kaggle.com/lokkagle/glassdoor-data, data Scraped form GlassDoor, contains over 1000 job descriptions of data scientist   
* Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model. 
* Built a client facing API using flask 

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, flask, json, pickle  
**For Web Framework Requirements:**  ```pip install -r requirements.txt```  




## Dataset - 
Contains 1000 job postings from glassdoor.com. With each job, we got the following:
*	Job title
*	Salary Estimate
*	Job Description
*	Rating
*	Company 
*	Location
*	Company Headquarters 
*	Company Size
*	Company Founded Date
*	Type of Ownership 
*	Industry
*	Sector
*	Revenue
*	Competitors 

## Data Cleaning
After choosing the right dataset, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Parsed numeric data out of salary 
*	Made columns for employer provided salary and hourly wages 
*	Removed rows without salary 
*	Parsed rating out of company text 
*	Made a new column for company state 
*	Added a column for if the job was at the company’s headquarters 
*	Transformed founded date into age of company 
*	Column for simplified job title and Seniority 
*	Column for description length 

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 



![alt text](https://github.com/hariranjanmeena/DS_salary_project/blob/d5ef391b0ebf0a3fe65e9a87d4e3ff4f037c3901/salary_by_job_title.PNG "Salary by Position")
![alt text](https://github.com/hariranjanmeena/DS_salary_project/blob/d5ef391b0ebf0a3fe65e9a87d4e3ff4f037c3901/positions_by_state.PNG "Job Opportunities by State")
![alt text](https://github.com/hariranjanmeena/DS_salary_project/blob/d5ef391b0ebf0a3fe65e9a87d4e3ff4f037c3901/correlation_visual.PNG "Correlations")
![alt text](https://github.com/hariranjanmeena/DS_salary_project/blob/d5ef391b0ebf0a3fe65e9a87d4e3ff4f037c3901/wordcloud_of_JobDesc.PNG "WordCloud of Job Description")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 11.37
*	**Linear Regression**: MAE = 19.65
*	**Ridge Regression**: MAE = 20.48




