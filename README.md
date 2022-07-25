# finalproject

## Deliverable 2


Description of:
- Prelim data preprocessing
Some data was dropped because it was obviously not useful for the machine learning model. This included data columns like the Zillow ID, the description of the house, and the home images links, all of which should have no real bearing on predicting home prices. Other data was dropped because it was redundant with other data we already had elsewhere. For example, there were three unique columns ('hasgarage', 'parkingspaces', and 'garagespaces') all describing the parking capacity of the homes; so an analysis was done to determine which column had the most accurate data, which turned out to be 'garagespaces', so the other two columns were dropped for the initial analysis. Finally, there were many columns related to the location of the house ('city', 'streetaddress', 'zipcode', 'latitude', 'longitude'). For this initial analysis, these were all dropped for two reasons: we needed more time to analyze which of these made the most sense to use for the ML model, and we wanted to see how accurate the ML model was based on other features not related to location. We will incorporate some of these location features when we start to optimize the existing ML model. 


- Prelim feature engineering and prelim feature selection, including decision-making process
After eliminating the more obvious and complicated features of the dataset, we used all other features in our initial machine learning models to see how they performed. This left us with 35 columns, or features, to test in our machine learning models (random forest regressor and multiple linear regression). One benefit of the random forest regressor model is that it has an attribute called 'feature_importances_' that gives a weight each of the model's features based on how impactful each feature is on the accuracy of the model. Based on this, we re-ran the model with only the top 9 features which improved the performanc of both models. That said, both models still need to be better optimized for them to be really useful in predicting housing prices in the Austin area.


- How data was split into training and testing sets
Since we are trying to predict housing prices in the Austin area, the 'latestprice' was our dependent variable; it's the closest datapoint we have to how much a house is worth based on certain characteristics. All other datapoints were considered independent variables that could potentially help predict home prices in the Austin area. 


- Explanation of model choice, including limitations and benefits
We chose the random forest regressor model and the multiple linear regression model for our top two machine learning models for this project. 


- Planned model improvements
