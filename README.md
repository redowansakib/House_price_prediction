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
data are missing correspondingly indicating absence of garage or Basement. Similarly, Whereas **Masonry Veneer Type** is 
missing the **Masonry Area** is 0 indicating absence of masonry. And all the other null values is assumed to be the 
absence of the house feature.

All the numerical and ordinal features has a non-normal distribution (D'Agostino Normality test). These features are 
mostly left skewed Neighborhood Feature has the highest cardinality with 25 categories. Though most of the categories has 5-8
categories. 

The density plot of the target variable (house price) shows a distribution that is positively skewed (skewed to the 
right). This is a common finding with price data and suggests that most houses are clustered at a lower price point, 
with a long tail of more expensive properties. 

### Step-2 Feature Engineering
#### Omission and Transformation
In the data there are 80 variables excluding target variable. There is `Id` variable which is dropped as it does not 
hold any predictive importance. variable `GarageYrBlt` represents the year at which garage of the house wes built. The
older the garage the less it will contribute to the overall price. To make this feature more relevant it is transformed 
with $\frac{1}{2025-GarageYrBlt}$. 
#### Imputation
From exploratory data analysis it can be inferred that **missing values correspond to absence of the house feature**. 
That is why constant value imputation (fill the `Null` value with a constant) is performed for categorical features with 'NA' and numerical features with 0 
except `CentralAir` and `Electrical` variable. `CentralAir` is a binary variable and the absence of `CentralAir` is 
already defined with 'N' so the constant value imputation is done with 'N'. And the `Electrical` variable can not be empty 
as no house can not be sold if it does not have electricity service. That is why mode imputation is used for `Electrical` 
variable.
#### Encoding
Ordinal features were populated with string representing it's rank. The ranks of each string for each variable is 
identified by `data_description.txt`. Categorical features are encode by target encoder for better performance and keeping
the dimensionality low of an already high dimensional dataset which one hot encoding would have worsened. 
#### Scaling 
The dataset is finally standardized to have mean 0 and 1 standard deviation 1.

