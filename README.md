# finalproject

## Barrett Gonzales Branch
## Deliverable One

For deliverable one I used two separate data sources in the form of csvs, austinHousingData.csv & austinHousingDetails. I changed the data structure of one column in excel but left all the other columns as is. Both data sources came from Zillow and had a common column which was “zpid”. I created both tables in Pg Admin and then imported both csvs. I combined the tables on the “zpid” column and then exported the data as a csv named austinHousingCombined.csv. I then used Jupyter notebook, specifically SQL Alchemy, to connect to PG Admin and import the table so that we can connect our ML model to the database directly. 
