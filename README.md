Using a competition dataset from Kaggle, I am creating a model to predict housing prices in Ames, Iowa. 

I will begin by thoroughly understanding the data and prepping it for models:

Some of the feature engineering performed includes:
  -changed multiple features from categorical strings to integer ratings.  Example: ratings of Excellent, Fair, and Poor have been changed to 5,3,1.
  -Filled in null values with an appropriate value.  Example: changing NaN to 'none' or 0 where appropriate.
  -Removed a single row with missing data that could not be estimated.
  -Engineered new features using a combination of existing features.  Examples:
                                                                          -Neighborhood Median Value rather than just a Neighborhood's name.
                                                                          -Median Price per Square foot by Neighborhood
  -OneHotEncoded features with string data
  -Created a DataFrame with only numerical features after transforming many of the original features to test the accuracy of simplifiing and limiting data.
  -Scaled all the data using StandardScaler
  
The data was then divided into Training, Validation, and Test sets.

I have ruled out Linear Regression and Decision Tree models.
A Random Forest Regressor has performed fairly well.

My best results have been achieved using stacked Gradient Boosting Regression.  I have one model that predicts fairly accurately across all price ranges.  I use those results as my base. I then created 3 new Gradient Boosting models for 3 price levels, up to 350K, between 350K and 500K, and over 500K.  If the  first model predicted a result below 350K, it was averaged with the new model using price level 1.  If the result from the first model predicted a price betweeen 350K and 500K, the result from the new model price level 2 was used to replace it.  Anything initially predicted over 500K was replaced with the prediction from price level 3.
