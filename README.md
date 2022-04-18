# **<span style='color:#0386f7de'>Predicting Heart Disease Based on Personal Key Indicators </b>**

Source data: [[Kaggle Database]](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease)

The presentation of this project can be accessed [[here]](https://github.com/ivn-m/predicting_heartdisease/blob/782d0eba60767ab90d0c36e300bbc5a88ab50d20/Green%20Team%20%20-%20Predicting%20Heart%20Disease%20EDIT.pdf)

## **<span style='color:#0386f7de'>Significance </b>**

Several health conditions, your lifestyle, your age and family history can increase your risk for heart disease. These are called risk factors. About half of all Americans (47%) have at least 1 of 3 key risk factors for heart disease: high blood pressure, high cholesterol, and smoking. Some risk factors for heart disease cannot be controlled, such as your age or family history. But you can take steps to lower your risk by changing the factors you can control [[Source: Center for Disease Control and Prevention]](https://www.cdc.gov/heartdisease/risk_factors.htm)

Detecting and preventing the factors that have the greatest impact on heart disease is very important in healthcare. Computational developments, in turn, allow the application of machine learning methods to detect "patterns" from the data that can predict a patient's condition.

## **<span style='color:#0386f7de'>Questions </b>**
1. Does sex/gender have an association with heart disease?
2. Is there an association between age & heart disease?
3. Are BMI, Smoking, Alcohol drinking, and prior stroke associated to heart disease?

## **<span style='color:#0386f7de'>Technologies Used </b>**

### Data Cleaning & Analysis:
The Pandas library will be used to clean the data and perform an exploratory analysis. Further analysis will be completed using Python.

### Database Storage:
Our database will be hosted in PostgreSQL, and will be populated from Jupyter Notebook using SQLite.

### Machine Learning
The SciKitLearn machine learning library will be used to create a classifier. Our training and testing setup is 70/30. 

### Dashboard
A functioning and interactive dashboard will be created using Tableau to present findings and results.

## **<span style='color:#0386f7de'>Machine Learning Model - Flow Chart</b>**

we plan to follow the steps of the following machine learning flow chart. This chart is subject to change and will be updated as we dive deeper into our analysis.

<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/d0e7d3ab8caac968acfb7920db42646918455b62/Predicting%20Heart%20Disease.png?raw=true"/>

## **<span style='color:#0386f7de'>Communication Protocols </b>**
- Team members will communicate using the #final-project Slack channel.
- Team members will meet at least 1x per week.
- Team members will plan next time they meet at the end of every meeting-- being flexible and open to each other's schedules.
- Team members will communicate with each other in the case they need internal deadline extensions or help with their part of the project.
- Team members will distribute work evenly amongst each other and be repsonsible for their distrib


## **<span style='color:#0386f7de'>Update on the status of the project </b>**

We have divided the project in several steps that are linked with the way this type of analysis have to be performed:

### **<span style='color:#0386f7de'>1- Explore the dataset </b>**
Degree of progress: 90% / 100%

We have worked exploring and analyzing the dataset to understand the information and its quality. A summary of the findings have been performed on Tableau for a better visualization:

Dashboard Stories: [[Heart Disease Stories]](https://public.tableau.com/app/profile/gustavo.alberto.diaz/viz/ETL-HeartDiseasePrediction-StoryBoard/DashboardDraft?publish=yes)

**General Overview of the Dataset**
<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/802f8dc42b1cd149315bbe1cb16ceb5260cf39f8/Resources/Images/Dashboard%20Draft.png?raw=true"/>

**Overview of the non-numeric Variables**
<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/ececdcb5940407445529fc983f4a0533087fb535/Resources/Images/Non-Numeric%20Variables.png?raw=true"/>

**Overview of the non-numeric Variables**
We are still working on the Tableau presentation for this type of variables.

### **<span style='color:#0386f7de'>2- Transform values and variables</b>**

We have analized and concluded that the dataset is quite clean and complete. There are not null variables and the data contained in the variables is consistent. The only variable where we found the need of cleaning is Sleeptime, where we found some data the could be considered as a mistake, as is shown on the graph below:

<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/802f8dc42b1cd149315bbe1cb16ceb5260cf39f8/Resources/Images/Sleeptime_whole.png?raw=true"/>

Considering that there are some responders with sleeptime higher that what we believe normal for a human been we decided to exclude the outliers by using the quantile method.

<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/802f8dc42b1cd149315bbe1cb16ceb5260cf39f8/Resources/Images/Sleeptime_Clean.png?raw=true"/>

The results obtained after the method have more sense (sleeping hours between 3 and 11 hours). By applying this method we have reduced the dataset in 4,523 rows which represents only 1,42% of the original dataset.

We have also used a correlation matrix to analyze which are the most correlated variables to predict a heart disease condition:

<p align = "left">
<img src ="https://github.com/ivn-m/predicting_heartdisease/blob/283864e73938e0bb03d108dcc99a4d11afc7658c/Resources/Images/Heat_Map.png?raw=true"/>

Finally we detect that the database is not balanced to perform a Machine Learning process: 

<p align = "left">
<img src =https://github.com/ivn-m/predicting_heartdisease/blob/283864e73938e0bb03d108dcc99a4d11afc7658c/Resources/Images/Confirming_Imbalance.png?raw=true"/>

We have decided to use the RandomOverSampler and RandomUnderSampler method to adjust the balance of the dataset.


### **<span style='color:#0386f7de'>3- Load the data into the model</b>**

We have loaded the dataset with the adjustments expresed in the previous step. We are in the process of analyzing if all the variables helps to predict heart disease or if we could have a better model with less variables involved.

### **<span style='color:#0386f7de'>4- Testing different Machine Learning Model</b>**

We have decided to test three different Machine Learning Model Methods: Confusion Matrix, Logistic Regresion and Random Forest Classifier. 

The best results have been achieved with the Random Forest Classifier method. Acheving the following eficiency values:

Accuracy 0.90790
Precision 0.84292
Recall 0.95356

### **<span style='color:#0386f7de'>5- Machine Learning Model Improvements</b>**

We are working on improving the model by excluding some variables that do not increase the quality of the prediction. We expect to finish this phase of the project by the endo of next week.

### **<span style='color:#0386f7de'>6- Conclusions and Comunication </b>**

We are confident on finishing our analysis and sharing our conclusions by the end of the next week. 



