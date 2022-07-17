# finalproject

### Roles of Team Members and Tasks for Deliverable 1:
1. Square- Molly
  - Create GitHub with branches and README.md
  - Created presentation (below) explaining project question, data info and communication protocol
  
2. Triangle- Claire
  - Created first draft of multiple linear regression ML model using partial/dummy data
  
3. Circle- Barrett
  - Set up first placeholder database
  - Connected DB and ML model placeholders
  
4. X- Zeena
  - Nothing for Dashboard on Deliverable 1
  - Working ahead by mapping out simple diagram of high level steps and technologies used for project

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

### Notes on Data Cleaning 

Redundant Columns to Drop:
- parkingSpace and garageSpace are mostly same column
  - Test in excel
- garageSpace and hasGarage columns are redundant, can drop hasGarage at least

Columns to Drop because Obviously Irrelevant:
- NumofCommunity features not well defined, maybe drop


Columns to Clean/Rows to Drop:
- Break down the frequency of home types, and decide if drop all rows besides Single Family housing 

New Columns to Create:
- New column that calculates age of the home based on yearBuilt?

### Question Answered

We hope to answer our question: can we predit housing prices in Austin, Texas based on a number of features. 

## Communication Protocols

### Roles of Team Members:
1. Square- Molly
2. Triangle- Claire
3. Circle- Barrett
4. X- Zeena

### Meeting Cadence

We are hoping to focus on collaboration during our class hours each week and will meet otherwise when needed. We have agreed to meet outside of class if needed to stay on track. Molly will meet individually with other team members on need-to-know basis to make sure she is documenting each step of the way. 

### GitHub

We are going to be using our github collaboration as our main hub for sharing our data. Each team member will have their own branch that others can view and give feedback on when necessary. We will push onto main branch when ready. 

### Slack

Lastly, we are using slack to share links or quick messages to keep everyone up to date with each step of the project. Henry, our TA, is also in our group message and will be able to help guide us along the way. 

### Google Drive

We are also sharing a Google folder for our Google slides and notes we take during class and project hours
