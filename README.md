# Capstone-Project--Retail-Sales-Prediction
![image](https://user-images.githubusercontent.com/93392791/200728066-374e3809-bec1-4143-aa59-7bfebaa367fe.png)

# 1. Business Problem.

## The Rossmann Sales Company

- A private drug store chain based in Germany, with main operations on Europe. Operates over 3,000 drug stores in 7 different contries.

- Offers heathcare and beauty product, including baby and body care, hygiene, cosmetics, dental hygiene, hair care, and so on.

- Business Model: Product sales.

## Problem

- The CFO wanted to reinvest in all stores, therefore, he need to know how much revenue each store will bring so he can invest it now.

## Goal

- Predict the daily sales of all stores for up to six weeks in advance.

## Deliverables

- Model's performance and results report with the following topics:

  - What's the daily sales in dollars for the next 6 weeks?
  
  - Predictions will be available through a Telegram Bot where stakeholders can acess the prediction by a smartphone

# 2. The Dataset
The dataset has 1017209 rows and 17 columns that represets features which explain behaviors of the target variable Sales.

- Id - an Id that represents a (Store, Date) duple within the test set

- Store - a unique Id for each store

- Sales - the turnover for any given day (this is what you are predicting)

- Customers - the number of customers on a given day

- Open - an indicator for whether the store was open: 0 = closed, 1 = open

- StateHoliday - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None

- SchoolHoliday - indicates if the (Store, Date) was affected by the closure of public schools

- StoreType - differentiates between 4 different store models: a, b, c, d

- Assortment - describes an assortment level: a = basic, b = extra, c = extended

- CompetitionDistance - distance in meters to the nearest competitor store

- CompetitionOpenSince[Month/Year] - gives the approximate year and month of the time the nearest competitor was opened

- Promo - indicates whether a store is running a promo on that day
 
- Promo2 - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating

- Promo2Since[Year/Week] - describes the year and calendar week when the store started participating in Promo2

- PromoInterval - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store

The dataset was split into training and validation sets.

The training dataset represets the sales between 2013-01-01 to 2015-06-19

The validation dataset represnts the last 6 weeks of sales which corresponde to the date 2015-06-19 to 2015-07-31

Since we validate our trained model, we can send it to "production", and the managers can access the sales predictions for the next six weeks.

# 3. Solution Strategy

## The strategy adopted was the following:

- Step 01. Data Description: I searched for NAs, checked data types (and adapted some of them for analysis) and presented a statistical description.

- Step 02. Feature Engineering: New features were created to make possible a more thorough analysis.

- Step 03. Data Filtering: Entries containing no information or containing information which does not match the scope of the project were filtered out.

- Step 04. Exploratory Data Analysis: I performed univariate, bivariate and multivariate data analysis, obtaining statistical properties of each of them, correlations and testing hypothesis (the most important of them are detailed in the following section).

- Step 05. Data Preparation: This step is necessary both for feature selection and for the machine learning models. Regarding the data types, numerical data was rescaled and categorical data was encoded.

- Step 06. Feature Selection: The statistically most relevant features were selected using the Boruta package. In the next steps, the machine learning models trained by using the features selected by Boruta presented a better generalizability performance.

- Step 07. Machine Learning Modelling: Some machine learning models were trained. The one that presented best results after cross-validation went through a further stage of hyperparameter fine tunning to optimize the model's generalizability.

- Step 08. Convert Model Performance to Business Values: In this step the model were analyzed from a business perpective, translating the errors into business values.

- Step 09. Deploy Model to Production: The model were deployed on a cloud environment to make possible that other stakeholders and services access its results.

# 4. Conclusion From Model Training
We were also curious about the total dataset (including sales= 0 rows). So we trained model using various algorithns and we got accuracy near about 92%.

We came to conclusion that removing sales= 0 rows actually removes lot of information from dataset as it has 172817 rows which is large and therefore we decided not to remove those values. We got our best RMPSE score from Random Forest model, we tried taking an optimum parameter so that our model doesn't overfit.

# Conclution from EDA

1) From plot sales competition open since month shows sales increasing from november and highest in month december.

2) From plot sales and a day of week, sales highest on monday and start declining from tuesday to saturday and on sundaysales almost near to zero.

3) Plot between promotion and sales shows that promotion helps in increasing sales.

4) Type of store place an important role in opening pattern of stores.

5) All type 'b' stores never closed except for refurbishment or other reason.

6) All type 'b' stores have comparitivly higher sales and it mostly constant with peaks appears on week ends.

7) Assortment level 'b' is only offered at store tybe 'b'.

8) We can observe that most of the stores remained closed during state holidays but it is interesting to note that the number of stores opened during school holidays were more than that were opened during state holidays.
