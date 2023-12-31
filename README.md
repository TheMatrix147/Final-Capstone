# Stress And Sleep Analysis

### By Derek Smith

## Project Overview Description:

#### Project Purpose: 
This project is intended to research the correlations and effects of stress on sleep duration and quality, and to verify distinct sleeping patterns that can occur as a result of stress. 
#### Background on Research Problem:
Many individuals suffer chronic symptoms of mild to severe insomnia, and this can be very disrupting to one's happiness, functionality, and
quality of life. Insomnia can be experienced by anyone for a number of underlying reasons. This analysis will specifically focus on determining whether or not stress levels are a potential cause of sleep disorders like insomnia. 
#### Existing Research: 
The datasets used in this analysis were sourced from kaggle.com, an open source dataset and data science platform. Research was done by the authors on several different factors that can influence sleep, including one's occupation, physical activity level, stress level, etc. In this analysis, particular interest is shown in the influence stress levels can have on sleep. Research was also done to detect different sleeping patterns based on certain variables such as a person's snoring rate, respiration rate, eye movement, etc. 

## Analysis Questions:

1. Is there a correlation between stress levels and sleep duration/quality?

2. Are there distinct sleeping patterns among individuals experiencing different stress levels?

3. Is there a cause-and-effect relationship between stress levels and sleep?

# Dataset Descriptions

### sleep_health.csv source: https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset

### Description:

[Sleep Health and Lifestyle Dataset](https://github.com/TheMatrix147/Final-Capstone/blob/main/dataset_descriptions/sleep_health_dataset_description.ipynb)

| Column | Datatype | Description |
| ---------| :---------:| ---------|
| person_id | int64 | Identifier for each individual |
|  gender  | object | Gender of person (Male/Female) |
| age | int64 | Age of person in years |
| occupation | object | Occupation or profession of person |
| sleep_duration   | float_64 | Number of hours person sleeps per day |
| quality_of_sleep | int64 | Subjective rating of the quality of sleep, ranging from 1 to 10 |
| physical_activity_level | int64 | Number of minutes person engages in physical activity daily |
|  stress_level  | int64 | Subjective rating of stress level experienced by person, ranging from 1 to 10 |
| bmi_category | object | BMI category of person (e.g., Underweight, Normal, Overweight) |
| blood_pressure | object | Blood pressure measurement of person, indicated as systolic pressure over diastolic pressure |
|  heart_rate  | int64 | Resting heart rate of person in beats per minute |
| daily_steps | int64 | Number of steps person takes per day |
| sleep_disorder | object | Presence or absence of a sleep disorder in person (None, Insomnia, Sleep Apnea) |

 
### Find_correlation.csv source: https://www.kaggle.com/code/ghsouvik2000/finding-correlation-between-stress-and-sleep

### Description: 

[Finding Correlation Dataset](https://github.com/TheMatrix147/Final-Capstone/blob/main/dataset_descriptions/finding_correlation_dataset_description.ipynb)

| Column | Datatype | Description |
| ---------| :---------:| ---------|
| snoring_rate | float_64 | Rate of person's snoring while sleeping |
| respiration_rate  | float_64 | Rate of person's breathing while sleeping |
| body_temperature | float_64 | Person's body temperature while sleeping  |
| limb_movement | float_64 | Rate of person's limb movement during sleep |
|  blood_oxygen  | float_64 | Person's blood oxygen levels while sleeping |
| eye_movement | float_64 | Person's eye movement during sleep |
| sleeping_hours | float_64 | Person's number of hours of sleep |
|  heart_rate  | float_64 | Person's heart rate while asleep |
| stress_level | int64 | Person's stress levels while sleeping (0 - low/normal, 1 – medium low, 2 - medium, 3 - medium high, 4 - high) |


# Exploratory Data Analysis

#### Summary Statistics
Using PANDAS methods, I analyzed the summary statistics and data types for both datasets. Missing data was also checked for. Based on the summary statistics, most of the variables in each dataset seem to follow a roughly normal distribution, with a few exceptions where there might be a slight skew. For each variable, a boxplot was created to better observe the nature of the distribution in greater detail according to its interquartile range.

#### Hypothesis Testing:
For the first dataset, the goal was to determine if a correlation existed between stress levels and sleep duration/quality. A hypothesis test was, therefore, conducted using the pearsonr and spearmanr python methods. A null hypothesis and alternative hypothesis were formed for both the sleep duration and sleep quality variables. The results of the pearsonr and spearmanr methods indicated that a very strong correlation exists between stress levels and sleep duration/quality. For the second dataset, the objective was to see if a correlation existed between stress levels and other variables that formed distinct sleeping patterns such as faster heart rate, lower body temperture, lower blood oxygen levels, etc. Using the pearsonr and spearmanr methods again, the results indicated that a very strong correlation also exists between stress levels and these variables. Hence, the null hypotheses were rejected. 

#### Basic Visuals
For the primary variables of concern in the first dataset, it was noted that sleep quality and duration decreased in a linear fashion as stress levels increased when the stress level variable was on the horizontal axis. For major variables in the second dataset, the snoring rate, respiration rate, limb movement, eye movement, and heart rate all increased linearly, while blood oxygen, body temperature, and sleeping hours decreased linearly when the stress level variable was on the horizontal axis. A scatterplot, KDE plot, and pairplot were all used to make these analyses. 

# Data Wrangling 

### Data Cleansing and Organization
For this section, I checked for any punctuation or spelling errors in column names, or for column names that needed to be made lowercase and snake case and changed those accordingly. I scanned for variables and data types that weren't matching and changed those data types to the correct ones. I checked for any missing values and filled those using the variable's mode. I also checked for outliers by creating boxplot visualizations and applying the zscore method. I ensured that both datasets followed a Tidy Data format. 

### Feature Engineering
For my first dataset, I used the one-hot encoding method/dummy variables to replace all nominal categories. This resulted in several new columns with boolean values in integer form. For my second dataset, no categorical variables needed to be re-expressed since all of the variables were quantitative. 

# Statistical Analysis

#### Hypothesis Testing:
For the first dataset, I formulated a null hypothesis and alternative hypothesis based on determining whether or not a cause-and-effect relationship exists between stress levels and sleep quality/duration. For the second dataset, I created a null and alternative hypothesis based on determining whether or not a cause-and-effect relationship exists between stress levels and distinct sleeping patterns such as more rapid eye and limb movements, and decreasing body temperature and blood oxygen levels. 

#### Regression Analysis:
For both datasets, a simple linear regression was performed to determine if stress levels really do have an effect on one's sleep quality/duration and sleeping patterns. After each regression, results for the model's r-squared, co-efficients, and p-value metrics were analyzed, all of which denoted for each regression that the models were significant and that stress levels indeed have an effect on the variables that were being tested. Thus, the null hypotheses were rejected. 

# Project Findings/Conclusion
Overall, the results of this project suggest that stress plays a major role in one's daily life of sleep. Not only can very strong correlations be seen between an individual's stress level and sleep quality/duration and sleeping patterns, but also an actual cause-and-effect relationship between each. 

In discussing potential shortfalls of the project, if it were someone's goal to perform a regression analysis that more fully explains the cause of sleep disorders, he or she would potentially want to test more than just one independent variable. Sleep disorders can be caused by many different factors other than stress. Thus, the explanatory power of the regression models used in my analysis would likely be deficient. In the case of my simple linear regressions, I only used the one input variable, stress level. Other variables affecting sleep could be added, like physical activity level, obesity, mental disorders, etc. to improve the model. 

Another point to consider for future analysis is to always work with complete information on the raw data used. Specifically, it is important that the data analyst knows how each variable is being measured based on the metrics provided. For example, if the variable being analyzed is eye movement, it should be clear that the activity is being measured in Hz (hertz). Or in the case of heart rate, the appropriate metric would be bpm (beats per minute). This will help to avoid any confusion or inacurracy in the analysis. In the case of the dataset used to identify distinct sleeping patterns in individuals experiencing different stress levels, no information was provided by the authors on the specific metrics that were being used for each variable. In the future, it will be better to work with a dataset that provides these metrics. 

This analysis proves to be of value because of the insight it offers on the effects of stress on sleep. The first part of the analysis showed evidence that stress levels do have a negative effect on one's ability to get restful sleep based on the outcome of the regression analysis that was done. The second part of the analysis showed potential evidence as to why stress levels have a negative impact on sleep. Based on the data given and its accompanying visualizations, the study suggested evidence that the body is in a fight-or-flight state and still quite active during sleep due to stress, as eye movement, limb movement, heart rate, respiration rate, and snoring rate increase, while blood oxygen levels decrease. In such a state, the body is not fully relaxed and able to settle down for the night, causing shorter, unrestful sleep and the distinct sleeping patterns just discussed. 

Because it is now clear that stress levels will negatively affect one's sleep, researchers and ordinary people can use this information to combat higher stress levels through helpful interventions. Thus, potential next steps that could be taken by researchers and scientists who seek to improve people's lives through stress-reduction strategies are to continue to look for those strategies and test them for effectiveness. Specifically, another analysis could be done on the effects exercise and meditation have on stress levels to see if these are potential solutions to problems like stress-induced insomnia.  




