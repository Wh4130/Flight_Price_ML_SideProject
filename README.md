# Flight_Price_ML_SideProject

This is Huang Lin, Chun's side project for machine learning: predict the flight price through the data scraped from the air ticket website.
Three routes between Tokyo and Taipei were chosen as my sample source.

## Project files

### 1_Scraping.ipynb

This Python markdown file is for scraping air tickets on Kayak.com. **Selenium** and **Beautiful** Soup modules were utilized to collect the data.
I collected flight data for four routes with respect to three airports (NRT 成田, HND 羽田, TPE 台北), including:

- NRT to TPE
- TPE to NRT
- HND to TPE
- TPE to HND

NRT to HND and HND to NRT were omitted, as the two airports are too close and there is no need for routes between them.
Four data frames in csv were generated in the Scraped Data and Graph folder.

### 2_Data_Preprocessing.ipynb

This file is for the data preprocessing before modeling. The following procedures were performed.

1. Combine the four data frames into one.
2. Split the observations with multiple airline companies into different observations.
3. Format the data.
   - Duration period to "minutes".
   - Price to numerical.
   - Date to "DateTime" format.
4. Deal with outliers.
5. Drop null values
6. One-hot encoding for categorical data.

### 3_Modeling.ipynb

This file is for training and testing the machine-learning model for flight price prediction.

#### Correlation Between Features

![output](https://github.com/Wh4130/Flight_Price_ML_SideProject/assets/90643963/3506a04c-353f-443c-89ee-1764ce4e405e)

#### Feature Importance

![output](https://github.com/Wh4130/Flight_Price_ML_SideProject/assets/90643963/72aecd59-4dc8-4b2f-b984-82cae67dbbdf)

We can see that air Average Price per Airline is the most relevant feature. The Average Price per Airline is the numerical tag for the airline company, so this result is intuitive, as price varies a lot across different airline companies.

#### Models

1. Linear Regression
2. Polynomial Regression
3. Lasso Regression
4. Ridge Regression
5. SVR
6. Decision Tree
7. Random Forest

After the training, the random forest model was the best model for predicting flight prices.

RandomForestRegressor(random_state=1)

Train score 0.775291825375477

Val score 0.7876189389702029

MAE: 29.921031009060588

MSE: 1681.908608944026

RMSE: 41.01107909997036

![output](https://github.com/Wh4130/Flight_Price_ML_SideProject/assets/90643963/d51aa7e4-423f-42e5-bdad-21c2e5c8cacd)

#### Hyperparameters Tuning

After tuning the hyperparameters of the random forest model, the best parameters were found to be:
- n_estimators = 100
- min_samples_split = 5
- min_samples_leaf = 2
- max_features = auto
- max_depth = 10

And the following is the scatter plot for predicted price and actual price after parameters tuning.

![output](https://github.com/Wh4130/Flight_Price_ML_SideProject/assets/90643963/84a1a38d-4f67-45a8-98fa-022232078dc0)

The final error metrics for the model are the following:

- MAE: 30.08669925429853
- MSE: 1679.2506685154378
- RMSE: 40.97866113619914












