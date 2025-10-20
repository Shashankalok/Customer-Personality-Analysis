

  
[*here you can download the cheatsheet*](https://www.kaggle.com/imakash3011/customer-personality-analysis)  

## Introduction   
For the given Kaggle Dataset, I will perform the exploratory data analysis with the help of customer segmentation. Customer segmentation will be carried out with the help of K-Means alogorithm. At the end of analysis I would like to answer some questions by gaining some insights from the data.  

## Technical      
- Language : Python (filetype: *.ipynb*)   
 
## Content 
Need to perform clustering to summarize customer segments.

## Data Field   
### People : 

| Variable Name | Description |
| --- | --- |
| `ID` | Customer's unique identifier |
| `Year_Birth` | Customer's birth year | 
| `Education` | Customer's education level |
| `Marital_Status` | Customer's marital status |
| `Income` | Customer's yearly household income | 
| `Kidhome` | Number of children in customer's household |
| `Teenhome` | Number of teenagers in customer's household |
| `Dt_Customer` | Date of customer's enrollment with the company |
| `Recency` | Number of days since customer's last purchase |
| `Complain` | 1 if customer complained in the last 2 years, 0 otherwise |

### Products :

| Variable Name | Description | 
| --- | --- |
| `MntWines` | Amount spent on wine in last 2 years |
| `MntFruits` | Amount spent on fruits in last 2 years |
| `MntMeatProducts` | Amount spent on meat in last 2 years |
| `MntFishProducts` | Amount spent on fish in last 2 years |
| `MntSweetProducts` | Amount spent on sweets in last 2 years |
| `MntGoldProds` | Amount spent on gold in last 2 years |

### Promotion :

| Variable Name | Description |
| --- | --- |
| `NumDealsPurchases` | Number of purchases made with a discount |
| `AcceptedCmp1` | 1 if customer accepted the offer in the 1st campaign, 0 otherwise |
| `AcceptedCmp2` | 1 if customer accepted the offer in the 2nd campaign, 0 otherwise |
| `AcceptedCmp3` | 1 if customer accepted the offer in the 3rd campaign, 0 otherwise |
| `AcceptedCmp4` | 1 if customer accepted the offer in the 4th campaign, 0 otherwise |
| `AcceptedCmp5` | 1 if customer accepted the offer in the 5th campaign, 0 otherwise |
| `Response` | 1 if customer accepted the offer in the last campaign, 0 otherwise |

### Place :

| Variable Name | Description |
| --- | --- |
| `NumWebPurchases` | Number of purchases made through the company’s web site |
| `NumCatalogPurchases` | Number of purchases made using a catalogue |
| `NumStorePurchases` | Number of purchases made directly in stores |
| `NumWebVisitsMonth` | Number of visits to company’s web site in the last month |

## What We Got From This Project
- **What are the statistical characteristics of the customers?**
- **What are the spending habits of the customers?**
- **Are there some products which need more marketing?**
- **How the marketing can be made effective?**
  
## Step Inside The Project
- **Exploratory Data Analysis (EDA)**
- **Machine Learning Model (K-Means)**
- **Cluster Interpretation**
- **Customer Distribution**
- **Relationship: Income VS Spendings**
- **Spending Habits By Clusters**
- **Purchasing Habits By Clusters**
- **Promotions Acceptance By Clusters**

## Conclusion
- Most of the customers are university graduates.
- Most of the customers are living with partners. 
- Those living alone have spent more than those living with partners.
- Most of the customers have only one child.
- Those having no children have spent more.
- Middle Age Adults, aged between 40 and 60, are famous age group category.
- Middle Age Adults are spending on average, more than the other age groups.
- Most of the customers are earning between 25000 and 85000.
- Wine and Meat products are very famous among the customers.
- On the basis of income and total spendings, customers are divided into 4 clusters i.e. Platinum, Gold, Silver and Bronze.
- Most of the customers fall into the Silver and Gold categories.
- Those who are earning more are also spending more.
- Most of the customers like to buy from store and then online from the web.
- Platinum customers showed more acceptance towards promotion campaigns while bronze customers the least interest.

## Answering Question
**What are the statistical characteristics of the customers?**<br>
The company's customers are mostly married. There are more Middle Aged Adults, aged between 40 and 60 and most of them like to have one child. Most of the customers hold   bachelor degree and their earnings are mostly between 25,000 and 85,000.<br>

**What are the spending habits of the customers?** <br>
Customers have spent more on wine and meat products. Those without children have spent more than those having children. Singles are spending more than the one's with the      partners. Middle aged adults have spent more than the other age groups. Store shopping is the preferred channel for purchasing among the customers. Web and Catalog            purchasing also have potential.<br>

**Are there some products which need more marketing?**<br>
Sweets and Fruits need some effective marketing. Company needs to run promotions for these products in order to increase the revenue from these products. Baskets of the      least selling products combined with the most selling products can be effective.<br>

**How the marketing can be made effective?**<br>
As a marketing recommendation give coupons to the old and high spending customers. Market the cheap and on-offer products to the low income and low spending customers. Web   purchasing has some potential. To unlock this give special discounts to the customers who sign up on company's website.<br>


1. What are missing values and how do you handle them?

Missing values occur when no data is recorded for a particular observation or feature.
In the Customer Personality Analysis dataset, some records had missing Income or Education values.

Handling methods:

Used .isnull().sum() to identify missing data.

If missing values were few, rows were dropped using .dropna().

If missing data was significant, we filled it using statistical methods like:

Mean/Median imputation for numerical columns (df['Income'].fillna(df['Income'].median(), inplace=True))

Mode imputation for categorical columns (df['Education'].fillna(df['Education'].mode()[0], inplace=True))

This ensures the dataset remains consistent without losing too much information.

2. How do you treat duplicate records?

Duplicate records can distort analysis results.
We checked duplicates using:

df.duplicated().sum()


Then removed them using:

df.drop_duplicates(inplace=True)


In this project, duplicate customer entries (based on ID or same demographic + purchase patterns) were removed to ensure each record represents a unique customer.

3. Difference between dropna() and fillna() in Pandas?
Function	Purpose	Example
dropna()	Removes rows or columns with missing values	df.dropna(inplace=True)
fillna()	Replaces missing values with specified values	df['Income'].fillna(df['Income'].median(), inplace=True)

Use dropna() when missing values are few or not important.

Use fillna() when you want to keep the data but replace nulls with suitable estimates.

4. What is outlier treatment and why is it important?

Outliers are extreme values that differ significantly from the rest of the data.
They can bias mean, standard deviation, and clustering results.

Treatment steps:

Detected using boxplots or z-scores:

from scipy import stats
df = df[(np.abs(stats.zscore(df['Income'])) < 3)]


Replaced or capped extreme values at percentile limits (e.g., 1st and 99th).

In this dataset, some customers had abnormally high spending or income values, which were treated to improve clustering accuracy (e.g., K-Means).

5. Explain the process of standardizing data.

Standardization scales data so that each feature contributes equally to analysis or machine learning models.

Steps:

Identify numeric variables (e.g., Income, MntWines, MntMeatProducts).

Apply StandardScaler() or MinMaxScaler():

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df_scaled = scaler.fit_transform(df[numeric_columns])


This ensures features have mean = 0 and standard deviation = 1.

In clustering (like K-Means), this prevents large-valued variables (like income) from dominating others.

6. How do you handle inconsistent data formats (e.g., date/time)?

Inconsistent formats can break analysis.
For example, Dt_Customer was stored as a string; we converted it into a proper datetime object:

df['Dt_Customer'] = pd.to_datetime(df['Dt_Customer'], format='%Y-%m-%d')


We also standardized categorical text (e.g., married, Married, MARRIED → all converted to lowercase “married”).

This ensures uniformity in data interpretation and calculation of variables like customer tenure or recency.

7. What are common data cleaning challenges?

Missing or incomplete data (e.g., missing income or education values)

Inconsistent formats (date, text case, numeric types)

Duplicate entries (same customer repeated)

Outliers and extreme values

Incorrect data types (e.g., numbers stored as strings)

Human entry errors or encoding issues

These challenges require careful inspection and decisions to maintain data integrity.

8. How can you check data quality?

We can evaluate data quality by performing these checks:

Completeness: Count missing values using .isnull().sum()

Uniqueness: Check duplicates using .duplicated().sum()

Validity: Verify data types (df.dtypes) and value ranges

Consistency: Ensure uniform formats for date/time, categories, etc.

Accuracy: Cross-check sample records for logical correctness (e.g., negative spending values)

Descriptive stats: Use .describe() to check unusual values or distributions

Maintaining data quality ensures reliable analysis, accurate clustering, and meaningful insights.



## [Click Here  for Visualize and Analyze](https://arienugroho050396.github.io/project7.html) :thumbsup: :thumbsup: :thumbsup:
<p align="center">
  <img width="460" height="300" src="https://www.icegif.com/wp-content/uploads/icegif-1436.gif">
</p>

  
   
 
