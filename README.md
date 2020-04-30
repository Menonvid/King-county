
## Mod 2 Project
# King County House Sale Prices

## Introduction
King County is a county located in the U.S. state of Washington. As of the 2019 estimate its population is approx 2,252,782. King is the most populous county in Washington, and the 13th most populous in the United States. The county seat is Seattle which is the state's largest city.

Key Questions:

Q1- What is the average cost of a house in King County?

Q2- Does Renovation have an effect on increasing the price of a house?

Q3- What are the important features to consider while selling a house?

Q4- How does the distance to a workplace effect the cost of a house?

Q5- Does having a waterfront view effect the price of a house?


Data description:
King County Dataset: 21597 rows x 21 columns

Categorical variables:

Condition: How good is the condition of the house on a scale of 1 to 5

Grade: values 1-13, rating of the house’s construction/design

Waterfront: House which has a waterfront

View: index 0-4, rating of the views from the house

Zipcode:zipcode

Continuous variables:

Price: Price of the house(USD)

Sqft_living: square footage of the house

sqft_lotsquare: square footage of lot

Sqft_above: square footage of house excluding basement

Sqft_living15: square footage of living space for the nearest 15 neighbors

Sqft_lot15: square footage of lot for the nearest 15 neighbors

Bedrooms: numbers of bedrooms

Bathrooms: number of bathrooms

Floors: number of floors in the house

Lat: latitude coordinate

Long: longitude coordinate

yr_built: Built Year
yr_renovated: Year when house was renovated

Exploratory Data Analysis:

Sqft vs Price of the house

Square footage (sqft) shows a positive correlation with price

The Project outlines the data analysis performed for conclusions and recommendations. The data analysis performed in the Project  observes the yearly and monthly trends to guage popular release times and genres and uses gross profit as an indicator for consumer interest.



Linear Regression Model:

A multivariate linear regression model was perfromed to predict house price with 80 variables:

 Set variables for modeling 
 y = 'price' 
 x_cols = ['bedrooms', 'bathrooms', 'sqft_living','floors','condition','yr_built', 'zipcode','sqft_living15', 'sqft_lot15', 'sqft basement']
 categorical_variables = ['floors', 'condition', 'zipcode']

 Create a DataFrame 
 df_ohe = pd.get_dummies(kc_housing[x_cols], columns= categorical_variables, drop_first =True)
 
 
 Use train_test_split from sklearn to split our data into X_train, X_test, y_train, y_test.

X_train, X_test, y_train, y_test = train_test_split(x_array, y_array_log, test_size=0.2, random_state=50)

Use LinearRegression() to find the best fit line and create a list of coefficients

Variables in our final model: 67 zip codes, sqft_living, sqft_living15, sqft_lot15, sqft basement, bedrooms, bathrooms, floors_1.5, floors_2, floor_3, and condition 2-5.

Results from model:

The mean of our R-squared values for our cross validation was 0.84; our model explains 84% of the variance.
Factors that caused an increase in house price:
An increase in number of bathrooms, sqft_living, sqft_living15, sqft_lot15, conditions (2-5)
Having a 1.5 floor
Factors that caused a decrease in house price:
An increase in bedrooms or sqft_basement
Houses with 2 or 3 floors
Location has a high impact on house price:
Top 3 zip codes with a high price factor: 98039, 98004, 98109

<h1>Findings</h1>

![](data/download.png)

Limitations & Further Research
We did not use factors like having a waterfront, quality of view, and year renovated. The top 3 zipcodes are located in areas with a waterfront so waterfront and view rating may have an impact on determining the value of the house

Further Research:

provide additional home quality insights by including:

Attribute a affluency value (tax rate) to zip codes

Prediction of house price in King County, USA


1.Introduction

King County is a county located in the U.S. state of Washington. As of the 2015 estimate its population was 2,052,800. King is the most populous county in Washington, and the 13th most populous in the United States. The county seat is Seattle which is the state's largest city.

      This paper addresses the following issues concerning the “price of house” with respect to the housing department of King county. In this paper, we investigate price of house in county and find out what are the factors responsible for different prices in different zones and different types of houses. And we tried to predict prices for houses and compared with those who already sold and got an idea for future sold houses.


2.Overview of study

       Our field study empirically investigates the pricing of house in king county, U.S.A. http://www.kingcounty.gov . King country have seashores and prices there are little high as compared to others. We empirically study how size, view, grade, location etc. can affect the house price. We analyzed lots of factors and had come to conclusion which consisted few factors. We estimated a regression of house prices in a multi-linear model. 

3.An empirical field study of house price in king county, USA
3.1 Overview
The specific objective of this Study was to investigate the pricing of houses employed in a different locale. This study analyzed house prices at King County, USA. Our goal was to compare prices of house with different location, different grades, different area etc. The rationale behind this is summarized next.





3.3 Model

We analyzed the research question using linear regression models. We established effect of size, parking, interior, location, local area, quality, ambiance on price of house and with data visualization and running few tests we came up with simplest model of our price prediction. We regressed the price accounting few variables.

Price of house  =  beta0  +  beta1 * sqft_living  +  beta2 * bedrooms  +      
                 beta3 * bathrooms  +  beta4 * grade  +  beta5 * sqft_above   
                +  beta6 * zipcode

We estimated Model 1A, using linear least squares.


3.4 Results

We found empirical support for H1. Price depended on size, interior, quality, outer areas and location of house.



<h1>Recommendations</h1>
The Production budget should be around 150 - 200 million USD.
Make an Action, Adventure, Sci-Fi or Animation movie which are our best genres.
The best season for the movies to release are during Summer or Spring.
The film should be around 2-3 hours and 1-2 hours if Animation.





