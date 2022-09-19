# **<span style='color:#0386f7de'>Predicting Heart Disease Based on Personal Key Indicators </b>**

Source data: [[Kaggle Database]](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease)

The presentation of this project can be accessed [[here]](https://docs.google.com/presentation/d/1V3dZCpzDp9Q2oq1DECRY6O3ylrlKOGtQVF9pc7DkagE/edit?usp=sharing)

Interactive Dashboard displaying Exploratory Analysis [[Dashboard]](https://public.tableau.com/app/profile/jhonatan.pirela/viz/ETL-HeartDiseasePrediction-DashboardV2/HeartDiseaseDashboard?publish=yes)


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

Finally we detect that the database is not balanced to perform a Machine Learning process. Class imbalanced is generally normal in classification problems. But, in some cases, the imbalance is quite acute where the majority class’s presence is much higher than the minority class. 

<p align = "left">
<img src =https://github.com/ivn-m/predicting_heartdisease/blob/283864e73938e0bb03d108dcc99a4d11afc7658c/Resources/Images/Confirming_Imbalance.png?raw=true"/>

Now that we have split our data into training and testing sets, we can scale the data using Scikit-learn's
The standard scaler standardizes the data. Which means that each feature will be rescaled so that its mean is 0 and its standard deviation is 1
![Scaling_Readme](https://user-images.githubusercontent.com/93852380/164817088-63b3ea66-7466-4ce1-a81b-3ee941115359.png)



We have decided to use the RandomOverSampler and RandomUnderSampler method to adjust the balance of the dataset. 

![Rebalancing_Dataset](https://user-images.githubusercontent.com/93852380/164569968-33e8eb7e-8574-4b64-a61b-04f4831cf61f.png)

Random oversampling involves randomly selecting examples from the minority class, with replacement, and adding them to the training dataset. Random undersampling involves randomly selecting examples from the majority class and deleting them from the training dataset.

### **<span style='color:#0386f7de'>3- Load the data into the model</b>**

We have loaded the dataset with the adjustments expresed in the previous step. We are in the process of analyzing if all the variables helps to predict heart disease or if we could have a better model with less variables involved. Modeling is an iterative process: you may need more data, more cleaning, another model parameter, or a different model. It's also important to have a goal that's been agreed upon, so that you know when the model is good enough.

### **<span style='color:#0386f7de'>4- Testing different Machine Learning Model</b>**

We have decided to test three different Machine Learning Model Methods: Confusion Matrix, Logistic Regresion and Random Forest Classifier. 

### Confusion Matrix:
![Confusion_Matrix_Readme](https://user-images.githubusercontent.com/93852380/164588917-60ede782-8c18-49f8-b33f-7c53022a6ac2.png)

### Logistic Regresion:
![Logistic_Regresion_Readme](https://user-images.githubusercontent.com/93852380/164588971-cb8f6dae-be09-4f7d-9680-5128ed6d56b3.png)

### Random Forest Classifier
![Random_Forest_Classifier_Readme](https://user-images.githubusercontent.com/93852380/164589055-0282f996-0386-447d-a728-5566bb9d876e.png)


The best results have been achieved with the Random Forest Classifier method. Achieving the following eficiency values:

Accuracy 0.9211621

Precision 0.863853

Recall 0.9602351

In summary, this model is one of the best one for predicting heart disease based on personal key indicators because the model's accuracy, 0.92, is high, and the precision and recall are good enough to state that the model will be good at  predicting heart disease.

### **<span style='color:#0386f7de'>5- Machine Learning Model Improvements</b>**


In the next steps we  improved the model by excluding some variables that do not increase the quality of the prediction. 

![Balanced_Random_Forest_Classifier_Readme](https://user-images.githubusercontent.com/93852380/164867591-b1d66150-2784-4cbf-bf8b-f2d1c1717e5c.png)

According to the results the Accuracy avg/total for the Precision is 0.88, for the Recall 0.86, for F1-Score 0.86, and support 52.6. 

### **<span style='color:#0386f7de'>6- Conclusions and Comunication </b>**

1. We performed a chi-square analysis to test if there is an association between gender and heart disease. We hypothesized that the distrubution of heart disease is equal amongst the genders.The p-value (p=0.0) of our chi-square analysis is below the 0.05 signinficance level, this we reject our null hypothesis. There is a difference in the distribution of heart disease amongst the genders.

2. We performed a chi-square analysis to test if there is an association between age category and heart disease. We hypothesized that the distrubution of heart disease is equal amongst the age groups. The p-value (p=0.0) of our chi-square analysis is below the 0.05 signinficance level, this we reject our null hypothesis. There is a difference in the distribution of heart disease amongst the different age groups.

3. We performed a multivaraite logistic regresstion test the  BMI, Smoking, Alcohol drinking, and prior stroke and their association to heart disease?


  
