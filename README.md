# Final Project

# Deliverable 1 

## Overview

### Selected topic:

Can we predict the housing price in the Austin area based on a number of factors?

### Reason they selected the topic:

As Austin based residents, we are curious to see if we can find any trends in our data that will help predict housing prices here in our city. We are looking forward to using this project as a chance to showcase our newly learned analytics styles. Along with the explanation of our data analysis, we will deliver a few visualizations to help tell our story.

## Data Info

### Description of the source of data

After searching for data on  current housing prices in the Austin area, we found a thorough and relatively clean set on Kaggle. A web scraper was used on Zillow to create this dataset. With four years of data and over 700 columns in the original dataset, we have the following information readily available:

- Identifiers: zillow id, address, zip codes
- Pricing: latest price, latest sale date
- Unique Factors: average school distance, average school rating

### Machine Learning Questions

- Should we run different models for different cities? Austin vs Pflugerville
- How can we run a Feature Extraction Model? 
- 17.8.1 Ensemble Learning and Decision trees - are these just for binary outcomes? Can I use them for predicting home prices?

## Question Answered

We hope to answer our question: can we predit housing prices in Austin, Texas based on a number of features?

## Communication Protocols

### Roles of Team Members:
1. Square- Molly
2. Triangle- Claire
3. Circle- Barrett
4. X- Zeena

### Meeting Cadence

We are hoping to focus on collaboration during our class hours each week and will meet otherwise when needed. We have agreed to meet outside of class if needed to stay on track. We will meet individually with other team members on need-to-know basis to make we are working through our project at the same speed. We are going to be using our github collaboration as our main hub for sharing our data. Each team member will have their own branch that others can view and give feedback on when necessary. We will push onto main branch when ready. Also, we are using slack to share links or quick messages to keep everyone up to date with each step of the project. Henry, our TA, is also in our group message and will be able to help guide us along the way. Lastly, we are also sharing a Google folder for our Google slides and notes we take during class and project hours.

# Deliverable 2

## Data Exploration Phase

During our first steps of looking at our CSV file, we wanted to understand our data. What are our variables? Are there any missing values? Do we need to transform any of the data so it can be uniform across the columns? Do we need to bring in any other datasets? Are there any outliers that will skew our data? Exploring the data actually helped us tighten up our research question. 

Exploring the data helped us tighten up our research question. [Zeena loaded in the CSV file](https://github.com/Mollyraeprice/finalproject/blob/zeena-dev1/prepro.ipynb) to explore the data in a few ways:
- She analyzed the data types
- Filtered to single family homes
- Checked for null values
- Filtered data only including Austin city
- Dropped columns with no importance
- Removed columns that couldn’t convert to numerical data
- Changed “latest_saledate” to a date format


### Database Setup

Both of our csv data sources came from Zillow and had the common column of "zpid". 

![Screen Shot 2022-07-20 at 7 04 20 PM](https://user-images.githubusercontent.com/98489681/180663991-03f30a66-f3e4-4241-972b-6a5fae43f8d3.png)

[Barrett](https://github.com/Mollyraeprice/finalproject/tree/barrett-dev1) created both tables ([1](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/data_source_one_final.jpg) and [2](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/data_source_two_final.jpg)) in pgAdmin and imported both CSVs. He combined the tables on the the "zpid" column and exported the data as a CSV called austinHousingCombined.csv. He jumped over to Jupyter Notebook next, imported SQL Alchemy so he could connect pgAdmin to [import the table](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/jupyter_database_load.jpg). Now, Claire has a database to connect to her ML model. 

#### Full Integrated Database

Barrett created a cloud-based database via Heroku. This was connected to the Prostgres database. After, he used SQL Alchemy to connect the https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/jupyter_database_load.jpg. He verified that the data from both Postgres and Herko matched in excel. After this process, our team was able to have access to this data. 

- [Database interfaces with the project](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/jupyter_database_load.jpg)
- Includes two tables ([1](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/data_source_one_final.jpg) and [2](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/data_source_two_final.jpg))
- Includes [a join](https://github.com/Mollyraeprice/finalproject/blob/barrett-dev1/sqlData.txt) using the database language


#### Variables

From the beginning, our variables were quite obvious:
- Identifiers: zillow id, address, zip codes
- Pricing: latest price, latest sale date
- Unique Factors: average school distance, average school rating


## Description of Analysis Phase

Once we had a good look at our data and Barrett connected the database to Jupyter Notebook, we started testing it in the machine learning model that Claire had built and tested previously. 

Compared Models:
- Random Forest Regression
- Linear Regression 

After comparing the accuracy of the ML models, the better performing model was now the new focus. 

## Machine Learning Model

### Preliminary data preprocessing 

Some data was dropped because it was obviously not useful for the machine learning model. This included data columns like the Zillow ID, the description of the house, and the home images links, all of which should have no real bearing on predicting home prices. Other data was dropped because it was redundant with other data we already had elsewhere. For example, there were three unique columns ('hasgarage', 'parkingspaces', and 'garagespaces') all describing the parking capacity of the homes; so an analysis was done to determine which column had the most accurate data, which turned out to be 'garagespaces', so the other two columns were dropped for the initial analysis. 

Finally, there were many columns related to the location of the house ('city', 'streetaddress', 'zipcode', 'latitude', 'longitude'). For this initial analysis, these were all dropped for two reasons: we needed more time to analyze which of these made the most sense to use for the ML model, and we wanted to see how accurate the ML model was based on other features not related to location. We will incorporate some of these location features when we start to optimize the existing ML model.

### Preliminary feature engineering selection

After eliminating the more obvious and complicated features of the dataset, we used all other features in our initial machine learning models to see how they performed. This left us with 35 columns, or features, to test in our machine learning models (random forest regressor and multiple linear regression). 

One benefit of the random forest regressor model is that it has an attribute called 'feature_importances_' that gives a weight each of the model's features based on how impactful each feature is on the accuracy of the model. Based on this, we re-ran the model with only the top 9 features which improved the performanc of both models. That said, both models still need to be better optimized for them to be really useful in predicting housing prices in the Austin area.

One task was to drop non-numeric columns and then run a weighted analysis on the remaining features to learn which of the columns we needed to drop or keep because of their importance. 

Our column, "latestPrice", represents the most recent prices these homes sold for. Therefore, Claire performed a boxplot to find any outliers in the prices. After seeing vast prices in the boxplot, she created buckets to divide the homes in different pricing categories. From our cheapest homes to the most expensive, we found that most homes cost between 100k to 3m. This is exactly what Claire was looking for. We have our new dataframe.

As we know, feature engineering helps line up the dataset with the machine learning model requirements. One of our ideas for feature engineering and selection was to add a new column of the calculated home and replace that with the yearBuilt for running the model. This will ultimately help the performance of the model.
We also dropped any homeType that isn’t a single family home. This resulted in us losing only 6% of our data. 

![Screen Shot 2022-07-20 at 7 38 03 PM](https://user-images.githubusercontent.com/98489681/180668858-b3382af3-72ed-466e-95a1-531095de29f1.png)

### Description of how data was split into training and testing sets

Since we are trying to predict housing prices in the Austin area, the 'latestprice' was our dependent variable as it represents represents the most recent prices these homes sold for; it's the closest datapoint we have to how much a house is worth based on certain characteristics. All other datapoints were considered independent variables that could potentially help predict home prices in the Austin area.

### Explanation of model choice, including limitations and benefits

We chose the random forest regressor model (RFR) and the multiple linear regression model for our top two machine learning models for this project.

Below are some advantages of using a RFR:
- it can used with data that differs in non-linear relationships
- it can run well on datasets that are large

Disadvantages:
- it won't explain the data very well
- overfitting could possibly happen
- it also needs some direction and tweeking 

The multiple linear regression model was used as a baseline to test against the RFR. We expect it to not perform as well as the RFR because linear models expect there to be a standard linear pattern between the independent variables and dependent variables. The RFR model can handle more non-linear relationships and still produce a good estimation. In short, RFR models are more robust when testing an unkonwn dataset for prediction problems unless you are very sure that a linear relationship exists, in which case a linear regression model would be fine to use.

Planned model improvements: 

- Drop any homeType that isn’t a single family home. We will only loose 6% of our data doing this, and the benefit will be that we are comparing the same types of homes which should improve the model performance.

- One of our ideas for feature engineering and selection is to add a new column of the calculated home and replace that with the yearBuilt for running the model. This is a much better metric than using the actual year that the home was built because this is technically not a time-series model, so the model will perform better using the scale of the age of the home vs the year built i.e. in the hundreds vs the thousands (e.g. 1 to 25 years old vs built in 1998-2021).

## Dashboard

Interactive dashboard link to tableau public:

https://public.tableau.com/views/dashboard1_16584263247130/Dashboard1?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link


### Description of interactive tools:
- Heat map of zip codes and housing prices
- Bar graph of month and price sold
- Bubble chart of price/lot size/ year built
- Line graph of price and average school rating

![Screen Shot 2022-07-24 at 1 31 25 PM](https://user-images.githubusercontent.com/98489681/180670273-76f0387e-a5e4-43d1-b9d2-c90e8d2b9a7e.png)

### Description of tools used to create final dashboard in a project map:
![Screen Shot 2022-07-24 at 4 36 21 PM](https://user-images.githubusercontent.com/98489681/180675933-d6ce1446-e44a-4944-93a0-c7a2696f8f52.png)

