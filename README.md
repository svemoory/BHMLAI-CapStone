### Project Title

Use machine learning models to identify different characteristics that make a Real Estate Agent successful.

### Author
Surekha Vemoory

### Executive summary

The California Bay Area is among one of the most competitive real estate markets in the United States with over 200k+ real estate agents. As a real estate technology company, we are responsible for providing various listing tools and services to our subscribers. We also offer statistical data and trainings on various subject to help our agents and brokers in the field. 

But can we predict how successful a real estate agent is going to be, by learning the traits of Top Agents? If we can identify the missing features of an agent, and can extend our services and trainings to better equip our subscribers. With the power of Machine Learning techniques, it is possible to analyze, regress, and classify large amounts of data through modeling and important features can be identified, and predictions can be made. There are two different angles to my analysis.

* Study the Agent Profile -  With subscribers classified as Top Agent vs Not, various machine learning classification models were run to extract the most important features that makes them successful. The accuracy of the best model is 72 out of 100. Subscribers with annual plans, serving multiple zip codes and profiles set as public are some of the important features of Top Agent.

* Study the Listing Data - Continuing with our business goal of helping agents succeed in the dynamic real estate market, another angle is to see what features in a home leads to faster sale. There are diverse set of features in a listing and its surroundings. If we extract the common features in the listings with least days on Market, it can help the agents project those features in their listings and also indicate potential hot markets based on geo location. The faster the home sells, agent can close more transactions. After running various models, highest accuracy was recorded as 37. The number of Open house is the most important feature that effects ow fast a home sells. Geographical location, living Sqft, age, and number of photos of the listing also has significant impact on the outcome.

Although, The ML models help answer the research questions to some extent, the lower accuracy suggests a lot of missing data. Collecting more relevant data from brokers like indicating the number of times list was shared on social media, marketing & staging budgets, number of leads generated, team vs individual representation of Buying/Selling Agents may help improve accuracy of listing models.

For agent profiling collecting the data related to Broker budget to train the Agents, the different types of tools and services that individual agents use, can substacially contribute to agent's success.

To summarize, although there is no perfect recipee that can define success in this dynamic market where economical factors like interest rates, inflation, and recession can definitely have effect of real estate market. But we can definitely create successful models that can identify the best set of features out of the data we have available.

If we can factor these as best practices and recommendations in our training and tools we offer, we can definitely help our subscriber's.

### Rationale

In this ever-changing landscape of real estate market, it is very difficult to navigate without a proper set of services and tools. As a technology company that serves agents/brokers across various California bay Area counties and provides them with listing information, services and training to succeed. But how do we target these trainings, tools and services to the set of subscribers who need them the most? 

Identifying the missing factors that can contribute to successful transactions can help us invest and align our tools, services, and training to appropriate subscribers, which can encourage them to extend their subscription.

### Research Question

What are the different characteristics that make a Real Estate Agent successful?

Can we predict how successful a real estate agent is going to be given a set of his/her profile features?

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

The confusion Matrix measures a model performance by visualizing the True and False predictions, and in this case it did produced good results.

![image](https://user-images.githubusercontent.com/28323151/226286395-5efc19a5-1bd6-4d50-9c68-51c96e51e473.png)

A comparison of all model with tuned parameters and their respective ROCAUC (receiver operating characteristic curve) score is given below.

![image](https://user-images.githubusercontent.com/28323151/226286672-684a0b2c-937b-471b-bc45-a2901424c588.png)

![image](https://user-images.githubusercontent.com/28323151/226288320-0a29b08d-b360-4542-ad38-69c840587164.png)

![image](https://user-images.githubusercontent.com/28323151/226287851-c4b9dd79-dd9d-4cd1-8453-bdb13243d591.png)
![image](https://user-images.githubusercontent.com/28323151/226289413-e4520d95-17a9-4c39-88a6-ab5643303b4e.png)
![image](https://user-images.githubusercontent.com/28323151/226294930-0e27702d-3a0d-4400-894e-8c3b485bca37.png)


### Results (Listing Regression)
 Full Dataset (125k listings)
 
 The listings in this dataset were distributed among 5 california counties. Te sales are more prominent in the months of April, May and June
 
 ![image](https://user-images.githubusercontent.com/28323151/226290838-dc2d5493-fc09-4778-a44a-1d2dbfa4d5e2.png)
 
 ![image](https://user-images.githubusercontent.com/28323151/226290990-c64eb0ea-9156-4d97-9e7c-5ff7e5284604.png)
 
 After removing the outliers and tuning various model, following observations were made
 
 ![image](https://user-images.githubusercontent.com/28323151/226291270-76d8181f-a6bf-4cae-ad0f-bf911d8931fd.png)
 
 Listing Dataset with Hot Months (78K listings)
 
 This dataset contains listings from various california counties for the months of April, May, and June months
 ![image](https://user-images.githubusercontent.com/28323151/226293119-30ecd620-578e-4073-b1f0-142027667f16.png)
Since, the heatmap did not reveal much correlation among features, Polynomial Features were used for better model accuracy. 
![image](https://user-images.githubusercontent.com/28323151/226293537-70ab8e99-5ecb-4fc4-bc82-508f30070555.png)

Principal Component Ananlysis was performed to capture minimum features with maximum variance. In this case, around 76% variance is captured wit 9 principal features.
![image](https://user-images.githubusercontent.com/28323151/226293804-72bfc755-28a1-4948-b676-7455e23b4cd2.png)

![image](https://user-images.githubusercontent.com/28323151/226294163-fa28a7ba-ea7a-492f-96dd-318a28eb2ab2.png)

![image](https://user-images.githubusercontent.com/28323151/226294281-0a40bde9-64a0-4ba4-8e84-f58b6e825647.png)


### Outline of project

[AgentClassification_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/AgentClassification.ipynb)

[ListingRegression_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/ListingRegression.ipynb)

[ListingRegressionHotMonths_JupyterNotebook](https://github.com/svemoory/BHMLAI-CapStone/blob/main/ListingRegressionHotMonths.ipynb)

### Contact and Further Information
Surekha Vemoory 
Email: surekha.vemoory@gmail.com
