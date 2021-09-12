# LENDING_CLUB_DEPLOYMENT

***

# Capstone Project- Lending Club

![Lending Club Logo](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/15afae8a-6480-4844-b1c8-4000464530bd.jpg)

## Introduction

"LendingClub is a US peer-to-peer lending company, headquartered in San Francisco, California. It was the first peer-to-peer lender to register its offerings as securities with the Securities and Exchange Commission (SEC), and to offer loan trading on a secondary market. LendingClub is the world's largest peer-to-peer lending platform." Wikipedia-Lending club
On the LendingClub platform, people invest on other people loan through an online secured system. On these types of platforms, in the most cases, the main criteria of giving loans to costumers is solely based on their credit scores, so that a customer with lower credit score (more risky) get higher rate and customer with higher credit score (less risky) get lower interest rate for their loan. Obviously, from the investor point of view, the loans with higher interest rate are more attractive due to their higher return of investment. However, it also has high risk of being not returned at all.
So, investing on "Bad loans" or charged-off, which means you loose your asset, is more worse than loosing an opportunity to gain more profit.
The machine learning/deep learning model that could predict which of the high interest loans are more likely to be returned, would bring added value by minimizing the associated risks. Also, using other factors along with credit score may help us to identify the high risky loans and minimize the investors loss of money more accurately.
Problem statement
In the last few years, applying for different types of loans through online peer-to-peer lending platforms such as the LendingClub is raising.

## Objective

1. First is to try to find a better prediction model to prevent investing on '"bad loans". To do that, First, going to implement some data engineering and preprocessing on LendingClub dataset to prepare data for analysis and modeling.
2. Second, need to apply explanatory data analysis (EDA) to investigate the features.
3. Preprocessed data on LendingClub loans labeled on whether or not the borrower defaulted (charged-off) to develop a model and predict whether or not a borrower will pay back their loan. This way in the future when we get a new potential customer who assigned with higher interest loan, we can assess whether or not they are likely to pay back the loan.

## Dataset

We used LendigClub Dataset possessing almost all features including FICO scores. This dataset contains more than several millions data and because, here, We only use a normal laptop to analyze and model this dataset, thus, We only selected the loans issued in 2018 (almost 0.5 million data) to reduce the processing time.

Moreover, some of the features in this dataset are only relevant after loans are issued and thus, not available at the moment of investing. For this reason, We used features list from here that are available and visible to investors before issuing a loan. To match this feature list to the main dataset, We did some simple and primary cleaning, whitespace removing, and spell corrections using dropping and “regular expression” technique. Also, it requires to check the unmatched features to see if some of them could be matched manually.

***


## DATA SEGMENTATION AND DATA CLEANING

•	In this project, we  have p prepared  a processed  dataset by   and  collected   the   clear-cut data available on https://www.kaggle.com/wordsforthewise/lending-club.

•	Using pandas data frame, we have calculated the percent of Non-null values in each columns.

•	Then removed the columns that had large number of Null value or were irrelevant to the analysis.

•	Then separated the columns with numerical values to those that have categorical values.

•	By using the fillna we have filled all the remaining numerical value columns with empty values with mean of the columns.

•	By using the fillna we have filled all the remaining Categorical value columns with empty values with mode of the columns.

•	After handling the null values, we deal with skewness of the data.

•	After checking the skewness, all the columns that are highly skewed are dropped using drop function.

•	Then we checked for outlier tendency using kurtosis. Then we capped some outlier.

•	Outliner were successfully handled. And after that we created the target variable that is Loan Status in this case.

•	Loan status had too many unique values so instead we created a new variable taking the default as 1 and rest 0.

•	We converted date object columns to integer years or months so that we can easily encode other categorical features

•	without exhausting our resources.

•	For filling the dates, we used the most used dates in that feature.

•	Thus our data cleaning process was cleared.

***

## EXPLORATORY DATA ANALYSIS:


### Average Load Amount vs Grade:
•	The graph draws a pattern between the loan amount and grade. As the Grade goes down from A to G, the Average Loan Amount linearly increases.
•	Additionally, it can be observed that the average loan amount of B grade loans is the least of all  grades.



### Loan Status diversification:

•	The count of fully paid is more than the charged off.
•	The dataset is slightly imbalanced and thus was balanced before the model training phase.

![Loan status values](https://user-images.githubusercontent.com/83585688/132972096-a6d2aa61-77a1-4f42-bf1c-1f2ac605982b.png)

               
### Box Plot for Loan Amount with Grades:

•	It can be inferred from the scenario that larger loans generally appear to be given at a lower grade, with the median loan amount for a grade G loan being almost 5000  higher  than  that    of    a grade A, B, or C loan.
•	Grade B, however, remains at the lowest in the range.
![Box Plot of Installment value vs  Loan Grade](https://user-images.githubusercontent.com/83585688/132972131-a4c3c603-1fc8-4256-8eca-96261b203a6f.png)


### Box Plot of DTI vs. Loan Grade:

  ![Box Plot of DTI vs  Loan Grade](https://user-images.githubusercontent.com/83585688/132972179-2e4aed21-f1de-4327-ae88-7ac734c0aea5.png)


### Box Plot Grouped By Terms:

  •	The  graph        shows   Interest  Rate    on  the  Y axis and term (number of months) on the x axis.
  •	On X axis-
    0: 36 months
    1: 60 months
  •	Interest    rates  are  based  on  term.  Larger amounts  were  seen  to  be  given  for  higher term. The rate  of interest  associated with them is also high.
 
 ![Box Plot Grouped By Terms](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/0190fbb2-416d-47e8-95b8-4dcc4e17edad.jpg )


### Loan Amount with respect to Grades:

  •	The graph is made between loan amount Grades from A to G, for two terms (36 months and 60 months).
  •	On X axis-
    0 denotes 36 months
    1 denotes 60 months
  •	Higher loan amount are associated with grade for longer terms.
  •	It can also be observed that marginally equal amount of loan was taken by all the Grades range for same terms.

![Loan Amount with respect to Grades](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/8b7ae079-27d5-44f6-926a-9d280001b330.jpg)

### Loan Amount vs Term: 

  •	The graph is made between loan amount and the term (number of months) for 3 types of Loan Status- Fully-paid, Charged- off, and Default
  •	Higher loan amount are associated with longer terms and see higher Charge Offs.

![Loan Amount vs Term](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/bb83377e-5617-48f7-90b3-bdc7caa11d2e.jpg)

***

### Training The Model:

Selecting the pivotal determinants from the accepted data frame, 22 specific columns are selected for optimizing the target variable i.e. whether the loan is to be approved or not.
Columns Selected for Training Model:

  	  loan_amt		  zip_code
  	 earliest_cr_line		  open_acc
  	  fico_score		  total_acc
  	  grade		  revol_util
  	  sub_grade		  target
  	  home_ownership		  issue_d
  	  installment		  credit_history
  	  int_rate		  credit_ratio
  	  mort_acc		  installment_ratio
  	  term		  annual_inc
  	  verification_status		  dti

***

## Models Used:

### 1.	Random Forest:

A random forest is a meta estimator that fits a number of decision tree classifiers on various sub-samples of the dataset and uses averaging to improve the predictive accuracy and control over-fitting.
•	Parameters Used
o	n_estimators : 10 ; defines the number of trees in the forest
o	random_state=10 ; Controls both the randomness of the bootstrapping of the samples used when building trees and the sampling of the features.
o	max_depth = 6; 

 Individual Account Result Table:

![Individual Account Result Table](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/ef8d4498-2b73-4bcc-9d01-e83fbe17aa2d.jpg)
 

 Joint Account Result Table:

![Joint Account Result Table](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/f85934a4-5340-4083-9087-f1bed0361b2c.jpg)


### 2.	Regularized Logistic Regression:

In the multiclass case, the training algorithm uses the one-vs-rest (OvR) scheme if the ‘multi_class’ option is set to ‘ovr’, and uses the cross-entropy loss if the ‘multi_class’ option is set to ‘multinomial’. This class implements regularized logistic regression using the ‘liblinear’ library, ‘newton-cg’, ‘sag’, ‘saga’ and ‘lbfgs’ solvers. 

•	Parameters Used:
o	penalty = ‘l2’ ;this is a Ridge regression which adds the squared magnitude of coefficient as penalty term to the loss function.
o	C = 100; it is the inverse of regularization strength
o	random_state = 0; 




Individual Account Result Table:

![Individual Account Result Table](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/3583cf0b-2529-46e3-bfd5-09bb163d74bd.jpg)

 

Joint Account Result Table:
 
![Joint Account Result Table](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/de292774-a3bb-46d4-81f5-dd0f34685991.jpg)
 

### 3.	Logistic Regression:

In Logistic Regression above performed, if no solver is mentioned i.e. ‘none’ is used, then regression is not applied.

•	Parameters used:
o	C = 1;
o	Solver = ‘none’;

### 4.	KNeighborsClassifier:

In k-NN, the output is a class membership. An object is assigned to a class that is most common among its k-neighbours.
•	Parameters used:
o	n_neighbors = 13; It defines the number of nearest neighbours considered.
o	P = 2; It is the power parameter. P=2 is used for Euclidean distance.
o	Metric= ‘euclidean’;

***

## Accuracy for Individual Account:
 
![Accuracy for Individual Account](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/9ee63630-5d0c-499f-b7ff-6fece8e294db.jpg)
 

## Results: 

Table 1. Accuracy For Different Models:

![Accuracy For Different Models](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/7898fff1-aed3-4b1f-94e1-fb24c9275e05.jpg)



## Conclusion :

Based on the results and the summary tables, Regularized Logistic Regression was selected for predictions ahead.

***

Now, we use flask framework to create a web app for our model.

we have created python file as "app.py" in our root folder. We will start working on web app now,

***
### Step-1

Initializing Flask object as per following command and importing requried liabraries.
***
### Step-2

Now, we load pickle files for Indivisual, Joint and sub grade model.
***
### Step-3

After loading all 3 files, we start with creating our web app.
we have 4 pages in web app, with help of '@app.route()' 
---
1. Main Page
    Our home page is pretty simple and plain.
2. Loand Prediction
    This page gives 2 option (Individual/Joint) to predict the loan for.
3. Individual Application
    Individual page asks for various inputs from the user to predict
4. Joint Application
    Joint page asks for various inputs from the user to predict.

***
### Step-4

***

Now, we take the inputs from user. This step is common for both Individual/Joint type.
Following is the list for inputs we ask from the user-

* Annual Income
* Fico score
* Earliest credit line
* Zipcode
* Total account
* Verification status
* Term
* Dti (Debt-to-income ratio)
* Loan amount
* MORTGAGE account
* Open account
* Revol Util
* Home Ownership

After getting all the inputs, we do feature engoneering in next step
***

### Step-5

**Feature Engineering**
 1. We convert datatype of all the input features to required datatypes to perform further steps.
 2. Now we calculate _credit ratio_
    **Credit Ratio = Open account / Total account**
 3. Calculate the _credit history_ of the applicant
    **Credit Histoy = Issue date - Earliest credit line**
 4. Predict _sub grade_ from *Fico score* using a **KNN model**
 5. With the help of _sub grade_ we decide **Grade**
 6. Now we calculate **intrest rate** and **EMI** on the basis of _Grade_ and _Loan amount_.
 7. Calculate **Installment Ratio** 
    **Installment Ratio = EMI / Loan amount**
 8. Now we merge all the features in one **final** array.
***
**Feature Scaling**
 We perform scaling on **Final** array using 'StandardScaler()'
***

### Step-6

**Model Building**
We use **Random Forrest** algorithm for our model.
Now, using _Final_ to train our model on it.

### Step-6

**Model Prediction**
Now, we use our model to predict the **Output** values.

We predict the loan status with the help of 3 parameters
--
 * DTI
 * Revol Util
 * Output
--
So, on the basis of these conditions we predict the loan status
 1. If **dti> 40.0**
    _loan is denied because your Debt to income is too high_
 2. If **revol_util>89**
    _loan is denied because your credit amount usage is too high_
 3. If **output > 0.43**
    _ loan is denied, your loan risk probabilty is high_

 Else, if all these conditions satisfy, _your loan will be approved_

***

## HEROKU DEPLOYMENT:


### Requirements:

Below you will find the requirements and prerequisites for the deployment.
•	Create account in Heroku
•	GIT installation
•	Heroku_CLI_installation
•	Login to Heroku account
•	Install gunicorn
•	Declare app dependencies
•	Create Procfile
•	Initialize git inside the project
•	Create_heroku_app
•	Add files to the GIT repository and deploy
•	Browse deployed URL
•	Download full project

How to make account in Heroku:
Step 1: To have an account in Heroku you have to login to https://signup.heroku.com/ 
Step 2: You must fill the mandatory details, as shown in the below screenshot.

![Form for Heroku signup](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/86bcbf27-4b64-4259-8cf6-52078bbc203a.jpg)

 
Step 3: Once you have verified your email address, you will be able to access the platform.
 
![Email Verification](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/287246bbd31c8a37ecbd9f306dc9104ab67029d0/Images/cf16a215-e22f-47ef-94b6-2031e0be7a9b.jpg)


## How to deploy a model on Heroku platform:


### 1.	Login to Heroku from command prompt
It will ask you to enter email id and password to login. After successful login next screen will show like below:

### 2.	Install gunicorn

Gunicorn is a Python WSGI HTTP Server for UNIX. It allows you to run any Python application concurrently by running multiple Python processes within a single dyno. The Gunicorn server is broadly compatible with various web frameworks, simply implemented, light on server resources, and speedy.
 
 ![Install gunicorn](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/9c761797f49b7bbf1531dff07f0cdd4ac5ece327/Images/Install%20Gunicorn.png)

### 3.	Declare app dependencies

Create requirements.txt file in the root directory of the project by pip freeze command. The requirements.txt file lists all the app dependencies together. When an app is deployed, Heroku reads this file and installs the appropriate Python dependencies using the pip install -r command.
 
 ![Declare app dependencies](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/9c761797f49b7bbf1531dff07f0cdd4ac5ece327/Images/Declare%20app%20dependencies.png)
 

### 4.	Create Procfile

The Procfile is always a plain text file that is named Procfile without a file extension in the root directory of the project, to explicitly declare what command should be executed to start your app.

F:\python-projects\flask-projects\flask-app\Procfile

![Declare app dependencies](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/9c761797f49b7bbf1531dff07f0cdd4ac5ece327/Images/Create%20Profile.png)

![Declare app dependencies-2](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/9c761797f49b7bbf1531dff07f0cdd4ac5ece327/Images/fff6b50d-ced6-4b8d-a402-4f2283548bc0.jpg)


 
A Heroku app’s web process type is special: it is the only process type that can receive external HTTP traffic from Heroku’s routers. If your app includes a web server, you should declare it as your app’s web process.
The first app refers to the filename app.py. The second app refers the instance of Flask which is inside app.py file.


### 5.	Initialize git

![Initialize git](https://github.com/BHAVI2803/LENDING_CLUB_DEPLOYMENT/blob/8bef92b62ec598623c18e2f2321c84984b1b72ea/Images/Initialize%20git.png)
 
### 6.	Create Heroku app, add files to GIT and deploy

### 7.	Browse deployed URL:

https://lendingclubloanriskpredict-api.herokuapp.com/

### 8.	Download full project

## Project Link: 
