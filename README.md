
## Mod 2 Porject
# King County House Sale Prices


## Introduction


Key Questions:
How much are houses selling for in King County?
How do features of a house affect its price?
How does the location of a house affect its price?


Data description:
King County Dataset: 21597 rows x 21 columns

Categorical variables:

Condition: index 0-5, rating of the house’s condition
Grade: index 1-13, rating of the house’s construction/design
Continuous variables:

Sqft_livingsquare: square footage of house's living space
sqft_lotsquare: square footage of lot
Sqft_above: square footage of house excluding basement
Sqft_living15: square footage of living space for the nearest 15 neighbors
Sqft_lot15: square footage of lot for the nearest 15 neighbors
Discrete variables:

Bedrooms: numbers of bedrooms
Bathrooms: number of bathrooms
Floors: number of floors (levels) in house
Variables dropped & reasonings:

Id: unique identifier for a house
Not a feature of the house
Date: house was sold
Not a feature of the house
Lat: latitude coordinate
Long: longitude coordinate
No meaningful information from one unit increase of lat or long to price
Waterfront: house which has a waterfront
17% non numerical values
View: index 0-4, rating of the views from the house
We were not able to find the grading scale for view to analyze it
yr_renovated: year when house was renovated
17,000 rows with 0.0 as values, we do not want to drop those rows
We cannot compare 0.0 (true vs false) to years (ex:1965-2015)
We could set yr_renovated to year built for houses that have not been renovated. However, we do not want to assume that a renovated house is the same as a newly built house
Exploratory Data Analysis:
Figure 1. Price distribution of houses



Figure 2: Square footage vs. Price of Houses

Square footage (sqft) shows a positive correlation with price; for each unit increase sqft, there is also an increase in the value of the house. Majority of the houses are under 4,000sqft and under $2M


Multivariate Linear Regression Model:
A multivariate linear regression model was perfromed to predict house price with 80 variables:

Create a dummy dataframe:

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

Hypothesis H1
            Price of house depends on its size, parking, interior, location, local area, quality, ambiance.

3.2 DATA 
For this exercise we collected data from www.kaggle.com which was originally pulled by government data directory of King County.
This data set contains house sale prices for King County, which includes Seattle. It includes homes sold between May 2014 and May 2015.

Id                     
      Id number (not relevant)
Date                    
      Date house was sold
Price                  
      Price of sold house( USD )
Bedrooms         
      Number of Bedrooms/House
Bathrooms
      Number of bathrooms/bedroom
sqft_living           
       square footage of the home
sqft_lot                
       square footage of the lot
floors            
       Total floors (levels) in house/house floor
waterfront          
       House which has a view to a waterfront
view      
        View rating on scale of 0 to 4
condition              
        How good the condition is ( Overall ) on scale of 1 to 5
grade                  
        grade of the house on the scale of 1 to 13
sqft_above           
        square footage of house apart from basement
sqft_basement     
        square footage of the basement
yr_built                  
        Built Year
yr_renovated         
        Year when house was renovated
zipcode             
         zipcode
lat                          
         Latitude coordinate
long                        
         Longitude coordinate
sqft_living15         
         Average square feet living area of 15 neighbor houses 
sqft_lot15        
         Average square feet lot area of 15 neighbor houses 




3.3 Model

We analyzed the research question using linear regression models. We established effect of size, parking, interior, location, local area, quality, ambiance on price of house and with data visualization and running few tests we came up with simplest model of our price prediction. We regressed the price accounting few variables.

Price of house  =  beta0  +  beta1 * sqft_living  +  beta2 * bedrooms  +      
                 beta3 * bathrooms  +  beta4 * grade  +  beta5 * sqft_above   
                +  beta6 * zipcode

We estimated Model 1A, using linear least squares.


3.4 Results

We found empirical support for H1. Price depended on size, interior, quality, outer areas and location of house.
This regression analysis also yielded beta1>0, with p <0.01 etc.




4 Conclusion

This paper was motivated by the need for research that could improve our understanding of how multiple vicinity factors influences the pricing in the housing industry. The unique contribution of this paper is that we investigated the price at which houses are sold by housing industry and related to what factors they select prices for various houses and how to predict prices using the past data for future.

This research has some important managerial implications. We can find cheapest house according to needs and on a seller’s perspective, we can decide which house will generate maximum profit with short-term visualization.









