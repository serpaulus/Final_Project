![Cover](https://user-images.githubusercontent.com/85421407/143089678-e61835f0-5d95-4c90-8425-9e6bdd60746c.png)

## Overview

Data analytics is an integral part of almost every industry today. These days It is hard to think of an industry in which Data Analytics does not play a major role.  The housing market, one the bedrocks of the economy, is not an exception. From analyzing national or regional market trends to being able to evaluate the home value before it enters the market; data analytics helps provide key insights that drive some of the most important market decisions and strategies. Real Estate, while being a very good investment, can also be very unpredictable.

As a team, we decided to study and analyze Housing Prices for Ames, Iowa as we all find it intriguing, considering how volatile and unpredictable the real estate market is, due to the impact of the pandemic. 

The goal of our project is to predict the Sale Price of the homes based on the features of each home. In this analysis, we hope to determine if there is any correlation between the home features and the final Sale Price.

Questions:

What is the predicted Sale Price for each home?

Is there any correlation between the Sale Price and the features?

What feature(s) has the most significant effect on the predicted final Sale Price?

What feature(s) has the least significant effect on the predicted final Sale Price?

What could we have done differently, to get better results?

What do we recommend for future analysis?


## Data Exploration

The dataset used for this project is the Ames, Iowa housing dataset found on Kaggle. The dataset is divided into two: training and test datasets. The training dataset has 1461 rows and 81 columns while the test dataset has 1459 rows and 80 columns. Initially, we selected 20 columns from the 81 features but the more we explored and cleaned the data, we dropped more features as they appear to have little impact on the Sale Price. 

   - [Test data set](https://github.com/serpaulus/Final_Project/blob/main/Data_Sets/test.csv)

   - [Train data set](https://github.com/serpaulus/Final_Project/blob/main/Data_Sets/train.csv)
   
   - [Qualitative summary](https://github.com/serpaulus/Final_Project/blob/main/Data_Sets/kaggle_data_description.txt)

   - [Test metadata summary](https://github.com/serpaulus/Final_Project/blob/main/Data_Sets/tst_desc.csv)

   - [Train metadata summary](https://github.com/serpaulus/Final_Project/blob/main/Data_Sets/train_desc.csv)
   

The main library used to import and clean the datasets was Python Pandas. Once completed, we exported the 20 cleaned dataset into the SQL database. We created features and an overall quality table, which we exported to SQL and merged to form a features/Quality table. The more we explored, the more we updated our dataset and dropped columns, which we will discuss in further detail.

## Machine Learning

When selecting home features for this analysis, we asked ourselves, what features do home buyers look for in their dream home? What features do we look for when buying a home and having our home appraised? What features do we believe will have the most correlation to the Sale Price? The answers to these questions were instrumental in the features we decided to explore. We selected House Style, No_of Bedrooms, Garage_Type, Total_Sqft, Lot Location, Year Built, Year Remodeled, 1st and 2nd Exterior, Masonry Veneer Type, Neighborhood, Overall Quality, Overall Condition, Sale Condition, and Sale price. 

The house dataset has several categorical values that need to be converted to numerical values to accurately analyze the data without errors. Using Label Encoder, we transformed the categorical values in the Dataframe to integers. See the [Machine Learning Analysis file]() for a complete description of the data clean-up and preparation process.

StandardScaler was used to scale the data and Seaborn was used to create a heatmap and check the correlation between the features and the Sale Price

![feature_corr_matrix](https://user-images.githubusercontent.com/85421407/142972745-45b22e35-672b-48a2-8ea8-5363f85b1238.png)

Based on the Heatmap, we can conclude that there is a correlation between the House Style and Sale Price. However, not all the figures are clear in the Heatmap. For better visualization, we created a correlation Scatter plot. Based on the results of the Scatter Plot, we can conclude that Total Square footage, Number of Baths and Overall Quality features also have strong correlation to the Sale Price, with Overall Quality having the strongest correlation.

![scatterplot_matrix](https://user-images.githubusercontent.com/85421407/142975667-e94d2f65-dcd0-4278-8a1c-feaae83d1ed6.png)

With these insights, we processed to set analysis with two methods Multiple Linear Regression and Random Forest. 

## Database

We created an [AWS DB instance](https://user-images.githubusercontent.com/85421407/142973441-79e27fed-3e89-4d6e-a320-d15a67af2310.GIF) called “housing-prices” and [using pandas and SQLAlchemy](https://github.com/serpaulus/Predicting_the_Final_Home_Price/blob/main/Resources/SQLDBpandas.GIF),([AWS RDS](https://github.com/serpaulus/Predicting_the_Final_Home_Price/blob/main/Resources/AWS%20RDS%20DB.png)) we connected AWS with SQL to store the working data for this analysis. Once connected, we imported and exported from the database throughout the project. Multiple tables were created during the duration of this project but for the final segment, we merged our updated clean_train table, which was renamed “df” with the price_compare table to properly display the features with the Actual and Predicted Sale Price. See [ERD](https://github.com/serpaulus/Predicting_the_Final_Home_Price/blob/main/Resources/ERD%20.png)
 schema.  


## Results

In our multiple linear regression analysis implementation, we attained the following results: 

r2: 0.767

Coefs: -5503.36095349 -7596.27583908 -6762.28060402 -1850.0864659
 44544.50977692 -1327.66270832 20832.54638433  1245.95433517
 -1633.18043178   848.12784225  2225.52109349  3685.52426009
 28548.80558026  6555.11431169  4062.03930574]

error: 38332.491698241436

Model adjustments are still required to improve accuracy.  

The following graph shows aids in comparing actual with predated sale prices.

![a](https://github.com/serpaulus/Predicting_the_Final_Home_Price/blob/main/Resources/MLR_results.GIF)

Random forest provided predictions, but the accuracy data showed inconsistencies with the implementation. Further development is required. 

[Machine_Learning_Model_MLR & RF](https://github.com/serpaulus/Predicting_the_Final_Home_Price/blob/main/Machine_Learning_Model_MLR_%26_RF.ipynb) contains the code used in this portion of the analysis.   

## Explore how house features affect the sale price [HERE](https://public.tableau.com/app/profile/ask1455/viz/PredicttheFinalHomePrice/Dashboard2_1?publish=yes)

[Project Presentation Slides](https://docs.google.com/presentation/d/1RFfQw3XB_AzRRkplmPbaM7PTO63AIKSM8Le8sRpE6ZY/edit?usp=sharing)

## Conclusion

Multiple linear regression is a tried an effective way to attain relatively reliable data predictions. Model adjustments are still required to improve accuracy. Nonetheless, with sampling corrections and better statistical feature analysis this model has potential for more accurate and precise results. Further, exploration of other models such as Random Forest and Neural Networks might also render higher versatility, and accuracy on this dataset.

