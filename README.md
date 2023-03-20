### Project Title

Use machine learning models to identify different characteristics that make a Real Estate Agent successful.

### Author
Surekha Vemoory

### Executive summary

### Rationale

In this ever-changing landscape of real estate market, it is very difficult to navigate without a proper set of services and tools. As a technology company that serves agents/brokers across various California bay Area counties and provides them with listing information, services and training to succeed. But how do we target these trainings, tools and services to the set of subscribers who need them the most? 

Identifying the missing factors that can contribute to successful transactions can help us invest and align our tools, services, and training to appropriate subscribers, which can encourage them to extend their subscription.

### Research Question

What are the different characteristics that make a Real Estate Agent successful?

Can we predict how successful a real estate agent is going to be given a set of his/her profile features

What are the most effective factors of a listing that lead to the lowest Days on Market or faster Sale? 

### Data Sources

In order to answer the research questions, 2 different datasets have been used from local MLS Data from year 2022. The first dataset consists of Agent profile info with features specific to around 18,000 agents in various California counties.

1. Agent Info - For Classification
```
TotalSales - (Numeric)Number of transactions in the last year  
saleVolume -  (Numeric) Total volumes of Sale for all transactions
License    - Real Estate License Number    
county     - County
AgentRole  - Broker,Agent
BrokerCode - Broker 
Biography  - y/n If biography entered in the public profile
Languages  - (Numeric)Number of spoken languages
Specialties - Other real Estate specializations
ZipCodesServed  - Number of zip codes served by the subscriber
SocialPlatform  - y/n If socially active in FB,twitter, instagram etc
AllowLeadsYN    -  
PhoneDisplayPublicYN  - y/n If contact number is public
productionpublicyn    -y/n
profilepublicyn      y/n If profile is published on xonsumer sites
FeePaid              y/n If delinquent on MLS fee
Experience           (Numeric) Number of years member of MLS
PlanType              Subscription Plantype
NumberofContacts      Number of contacts (leads) in Matrix
Photo                y/n If Profile includes photo
TopAgent   - y/n Classified as the top 20% list of Agents 
```
The second dataset consists of various features of listings from the last 10 years (initially) and 5 years (filtered on hot months) from MLSData

2. Listing Info - For Regression
```
SaleoverListPrice    % Sale over list price
ListPrice    
SalePrice    
CountyName    Geographical county
LivingSqFt    Total living square footage
WalkScore    distance to nearby businesses
Subclass    Single Family/Townhome/Condo
LotSize    Approx lot size
DaysOnMarket    Number of days listing has been on market
CloseTime    Days before listing went pending
SaleRate    Difference of Max DOM and actual DOM(until Pending)
CloseRate    Difference of Max DOM and actual DOM (until Date of Escrow)
PostalCode    Listing zip code
Age    Current - Year built 
BedsTotal    beds
BathsFull    full baths
ListingAgentLicenseID    
ListDate
SaleMonth
Latitude    geo location
Longitude    geo location
PhotoCount    Number of listing photos
VirtualTour    
OpenhouseHours    Number of open house hours
OpenhouseCt    Number of open house
tourCt    Number of tours
ElementarySchoolRating    
HighSchoolRating   
GarageSpaces
IncorporatedYN
HOAExistYN
FireplaceYN
PoolYN
NewConstructionYN
```
### Methodology

To frame the task, a standard process in industry for data projects called CRISP-DM is followed. The framework has multiple phases.
![image](https://user-images.githubusercontent.com/28323151/226245695-e85daf82-4926-452f-a708-be375bfcaa9f.png)

Business Understanding - This initial phase focuses on understanding the project objectives and requirements from a
business perspective, and then converting this knowledge into identifying the key objectives. 

Data Understanding - In this phase initial data is collected and activities in order to get familiar with the data and to identify data
quality problems are performed.

Data Preparation - The data preparation phase covers all activities to construct the final dataset (data that will be
fed into the modeling tool(s)) from the initial raw data. Outliers are identified and eliminated and various features are transformed and scaled.

Modeling - In this phase, various modeling techniques are selected and applied, and their parameters are
calibrated to optimal values.

For Classification problem on the agent info dataset, various modeling techniques have been used Logistic Regression, K Nearest Neighbor,
Decision Tree, and Support Vector Machine 

For Regression problem on the listing dataset, the following modeling techniques have been used Linear Regression, Ridge Regreesion, TransformedTargetRegressor, Random Forest. 

Evaluation - During this phase, one or more models that appear to have high quality, were analyzed and Gridsearch technique was used to select optimal hyperparameteres to tune the models furter. Polynomial Features were used along with Principal Component Analysis to pick the important features that effects the target variable. In some cases ensemble techniques such as Voting Classifier and Gradient Boosting were used to achieve better model accuracy.

Deployment - The results from the analysis are summarized in a report that can be used by the business make predictions and understand the missing features that can further produce useful results.

### Results (Agent Classification)

The Agent Profile dataset has extremely imbalanced target variable. The heatmap of the various features was plotted to visualize correlation among various features.
![image](https://user-images.githubusercontent.com/28323151/226283319-dcce019b-e30e-42f5-bfaa-5b0c448e972b.png)
![image](https://user-images.githubusercontent.com/28323151/226284062-c4eba45a-8600-4118-a853-379f57974259.png)
Most of the agents are serving the Santa Clara county
![image](https://user-images.githubusercontent.com/28323151/226284436-92115367-5f07-4c42-a8e6-f67c5007d752.png)

The initial results produced by various classification model with default values, indicate Decision Tree to be the best model with training set but LOgistic Regression performed better on the test set

![image](https://user-images.githubusercontent.com/28323151/226286072-411a4ee6-a85a-4583-a39b-a48bc6fca9e0.png)

After tuning the various classifiers using gridsearch, KNN performed better with ROCAUC score of 72. The best params are {'knn__n_neighbors': 9}

Logistic regression train and test accuracy were not optimal but with ROCAUC score of 68 it was the second best model. The best params were {'lgr__C': 0.1, 'lgr__penalty': 'l1', 'lgr__solver': 'liblinear'}

![image](https://user-images.githubusercontent.com/28323151/226286395-5efc19a5-1bd6-4d50-9c68-51c96e51e473.png)

A comparison of all model with tuned parameters and their respective ROCAUC (receiver operating characteristic curve) score is given below.

![image](https://user-images.githubusercontent.com/28323151/226286672-684a0b2c-937b-471b-bc45-a2901424c588.png)

![image](https://user-images.githubusercontent.com/28323151/226288320-0a29b08d-b360-4542-ad38-69c840587164.png)

![image](https://user-images.githubusercontent.com/28323151/226287851-c4b9dd79-dd9d-4cd1-8453-bdb13243d591.png)
![image](https://user-images.githubusercontent.com/28323151/226289413-e4520d95-17a9-4c39-88a6-ab5643303b4e.png)


### Results (Listing Regression)



### Outline of project

[AgentClassification_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/AgentClassification.ipynb)

[ListingRegression_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/ListingRegression.ipynb)

[ListingRegressionHotMonths_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/ListingRegressionHotMonths.ipynb)

### Contact and Further Information
Surekha Vemoory 
Email: surekha.vemoory@gmail.com
