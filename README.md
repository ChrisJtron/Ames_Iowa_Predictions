Using a competition dataset from Kaggle, I am creating a model to predict housing prices in Ames, Iowa.

After a few false starts and realizing I did not know as much as I thought I did, I am starting over with a more organized approach and the aid of a book 

I will begin by thoroughly understanding the data and prepping it for models:

Some of the feature engineering performed includes:
  -changed multiple features from categorical strings to integer ratings.  Example: ratings of Excellent, Fair, and Poor have been changed to 5,3,1.
  -Filled in null values with an appropriate value.  Example: changing NaN to 'none' or 0 where appropriate.
  -Removed a single row with missing data that could not be estimated.
  -Engineered new features using a combination of existing features.  Examples:
                                                                          -Neighborhood Median Value rather than just a Neighborhood's name.
                                                                          -Median Price per Square foot by Neighborhood
  -Removed outliers with exceptionally high Sale Prices and Square Footage
  -OneHotEncoded features with string data
  -Created a DataFrame with only numerical features after transforming many of the original features.
  -Scaled all the data using StandardScaler
  
I have also created an area in my code to remove features based on their correlation (R2 values) to the target.  The R2 value can be changed to test models using data with different levels of correlation.

The data was then divided into Training, Validation, and Test sets.

I have ruled out Linear Regression and Decision Tree models.
A Random Forest Regressor has performed fairly well.
The most promising model so far is an Elastic Net with Scaled Polynomial features.
