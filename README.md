# House_price_prediction

This Repository contains my attempts to climb the leaderboard of the kaggle competition named 
<a href=https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques>'House Prices - Advanced Regression Techniques'</a>.
It provides me with two dataset one train.csv and the other test.csv where I have to train my models by train.csv data and
generate a prediction on test.csv data for submission. Description of the data can be found <a href=''>here</a>.
<br>

### Step-1: Exploratory data analysis
The train data has 1460 observations, 79 features and 1 target variable. There are 22 categorical Features, 36 numerical 
features, 21 ordinal features and 1 binomial feature.

A routine exploratory analysis of the data reveals some systematic missing data. All the **Garage** and **Basement** 
data are missing correspondingly indicating absence of garage or Basement. Similarly Where as **Masonry Veneer Type** is 
missing the **Masonry Area** is 0 indicating absence of masonry. And all the other null values is assumed to be the 
absence of the house feature.

All the numerical and ordinal features has a non-normal distribution (D'Agostino Normality test). These features are 
mostly left skewed Neighborhood Feature has highest cardinality with 25 categories. Though most of the categories has 5-8
categories. 

The density plot of the target variable (house price) shows a distribution that is positively skewed (skewed to the 
right). This is a common finding with price data and suggests that most houses are clustered at a lower price point, 
with a long tail of more expensive properties. 


