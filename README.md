# finalproject

## Deliverable 2


Description of:
- Prelim data preprocessing
Some data was dropped because it was obviously not useful for the machine learning model. This included data columns like the Zillow ID, the description of the house, and the home images links, all of which should have no real bearing on predicting home prices. Other data was dropped because it was redundant with other data we already had elsewhere. For example, there were three unique columns ('hasgarage', 'parkingspaces', and 'garagespaces') all describing the parking capacity of the homes; so an analysis was done to determine which column had the most accurate data, which turned out to be 'garagespaces', so the other two columns were dropped for the initial analysis. Finally, there were many columns related to the location of the house ('city', 'streetaddress', 'zipcode', 'latitude', 'longitude'). For this initial analysis, these were all dropped for two reasons: we needed more time to analyze which of these made the most sense to use for the ML model, and we wanted to see how accurate the ML model was based on other features not related to location. We will incorporate some of these location features when we start to optimize the existing ML model. 

Our column, "latestPrice", represents the most recent prices these homes sold for. Therefore, Claire performed a boxplot to find any outliers in the prices. After seeing vast prices in the boxplot, she created buckets to divide the homes in different pricing categories. From our cheapest homes to the most expensive, we found that most homes cost between 100k to 3m. This is exactly what Claire was looking for. We have our new dataframe.


- Prelim feature engineering and prelim feature selection, including decision-making process
After eliminating the more obvious and complicated features of the dataset, we used all other features in our initial machine learning models to see how they performed. This left us with 35 columns, or features, to test in our machine learning models (random forest regressor and multiple linear regression). One benefit of the random forest regressor model is that it has an attribute called 'feature_importances_' that gives a weight each of the model's features based on how impactful each feature is on the accuracy of the model. Based on this, we re-ran the model with only the top 9 features which improved the performanc of both models. That said, both models still need to be better optimized for them to be really useful in predicting housing prices in the Austin area.


- How data was split into training and testing sets
Since we are trying to predict housing prices in the Austin area, the 'latestprice' was our dependent variable as it represents represents the most recent prices these homes sold for; it's the closest datapoint we have to how much a house is worth based on certain characteristics. All other datapoints were considered independent variables that could potentially help predict home prices in the Austin area. 


- Explanation of model choice, including limitations and benefits
We chose the random forest regressor model (RFR) and the multiple linear regression model for our top two machine learning models for this project. 

Below are some advantages of using a RFR:
- it can used with data that differs in non-linear relationships
- it can run well on datasets that are large

Disadvantages of RFR:
- it won't explain the data very well
- overfitting could possibly happen
- it also needs some direction and tweeking 

The multiple linear regression model was used as a baseline to test against the RFR. We expect it to not perform as well as the RFR because linear models _expect_ there to be a standard linear pattern between the independent variables and dependent variables. The RFR model can handle more non-linear relationships and still produce a good estimation. In short, RFR models are more robust when testing an unkonwn dataset for prediction problems unless you are very sure that a linear relationship exists, in which case a linear regression model would be fine to use. 

- Planned model improvements

1. Drop any homeType that isn’t a single family home. We will only loose 6% of our data doing this, and the benefit will be that we are comparing the same types of homes which should improve the model performance.

2. One of our ideas for feature engineering and selection is to add a new column of the calculated home and replace that with the yearBuilt for running the model. This is a much better metric than using the actual year that the home was built because this is technically not a time-series model, so the model will perform better using the scale of the age of the home vs the year built i.e. in the hundreds vs the thousands (e.g. 1 to 25 years old vs built in 1998-2021).
