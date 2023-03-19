### Project Title

Use machine learning models to identify different characteristics that make a Real Estate Agent successful.

**Author**
Surekha Vemoory

#### Executive summary

#### Rationale

In this ever-changing landscape of real estate market, it is very difficult to navigate without a proper set of services and tools. As a technology company that serves agents/brokers across various California bay Area counties and provides them with listing information, services and training to succeed. But how do we target these trainings, tools and services to the set of subscribers who need them the most? 

Identifying the missing factors that can contribute to successful transactions can help us invest and align our tools, services, and training to appropriate subscribers, which can encourage them to extend their subscription.

#### Research Question

What are the different characteristics that make a Real Estate Agent successful?

Can we predict how successful a real estate agent is going to be given a set of his/her profile features

What are the most effective factors of a listing that lead to the lowest Days on Market or faster Sale? 

#### Data Sources

In order to answer the research questions, 2 different datasets have been used from local MLS Data from year 2022. The first dataset consists of Agent profile info with features specific to around 18,000 agents in various California counties.

1. Agent Info - For Classification

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

The second dataset consists of various features of listings from the last 10 years (initially) and 5 years (filtered on hot months) from MLSData

2. Listing Info - For Regression

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

#### Methodology
Various Regression Techniques like Linear, Lasso, Ridge and Ensemble 

#### Results
What did your research find?

#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


##### Contact and Further Information
Surekha Vemoory 
Email: surekha.vemoory@gmail.com
