# finalproject

## Barrett Gonzales Branch
## Deliverable One

For deliverable one I used two separate data sources in the form of csvs, austinHousingData.csv & austinHousingDetails. I changed the data structure of one column in excel but left all the other columns as is. Both data sources came from Zillow and had a common column which was “zpid”. I created both tables in Pg Admin and then imported both csvs. I combined the tables on the “zpid” column and then exported the data as a csv named austinHousingCombined.csv. I then used Jupyter notebook, specifically SQL Alchemy, to connect to PG Admin and import the table so that we can connect our ML model to the database directly.

## Deliverable Two

For deliverable two, I created a cloud-based database via Heroku. I connected the new Heroku database to my Postgres database. I used SQL Alchemy to connect the Heroku database to Jupyter (see database_connection.ipynb)and downloaded the relevant data.  I conducted various verifications via excel to ensure that the data from Postgres matched the Heroku data that was imported in Jupyter. My teammates then ran various queries via the connection provided to ensure that the proper accesses were set up and everyone had access to the relevant data.
