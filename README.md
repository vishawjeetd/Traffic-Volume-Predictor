
![Logo](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/traffic.png?raw=true)


# Traffic Volume Prediction Hackathon


Welcome to the Traffic Volume Prediction Hackathon repository! In this project, we aimed to predict traffic volume on roadways using various machine learning models. We conducted exploratory data analysis (EDA), data cleaning, and feature engineering to prepare the dataset for modeling. After extensive testing across multiple models, we selected the best-performing model for traffic volume prediction.


[Get more details on Kaggle](https://www.kaggle.com/competitions/123ofai-predict-the-traffic-volume/overview)




## Quick Data Overview

- **Files**:
    -  train_set_dirty.csv - the training set with input features and GT value for 'traffic_volume'

    - test_set_nogt.csv - the test set with only input features to evaluate your model (from which you shall generate the output file)
    - sample_submission.csv - a sample submission file in the expected format

- **Columns**:
    - holiday: a categorical variable that indicates whether the date is a US national holiday or a regional holiday (such as the Minnesota State Fair).
    - temp: a numeric variable that shows the average temperature in kelvin.
    - rain_1h: a numeric variable that shows the amount of rain in mm that occurred in the hour.
    - snow_1h: a numeric variable that shows the amount of snow in mm that occurred in the hour.
    - clouds_all: a numeric variable that shows the percentage of cloud cover.
    - weather_main: a categorical variable that gives a short textual description of the current weather (such as Clear, Clouds, Rain, etc.).
    - weather_description: a categorical variable that gives a longer textual description of the current    weather (such as light rain, overcast clouds, etc.).
    - date_time: a DateTime variable that shows the hour of the data collected in local CST time.
    - traffic_volume: a numeric variable that shows the hourly I-94 reported westbound traffic volume.

## EDA Insights

During the exploratory data analysis (EDA) phase, we uncovered several key insights about the dataset:

1. **Duplicates at *date_time* level:** We identified duplicates within the dataset at the *date_time* level, which may require further investigation and cleaning to ensure data integrity.

2. **Incorrect mapping of *holiday* data:** The *holiday* feature was found to be incorrectly mapped. Correcting this mapping is crucial for accurate analysis and model training.

3. **Cyclical nature of data based on hours:** Analysis revealed a cyclical pattern in traffic volume based on hours of the day, indicating potential hourly trends that could be leveraged in modeling.

   ![date_time_analysis_with_traffic_volume](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/traffic_volume_by_datetime.png?raw=true)

4. **Relationship between *weather_main* and *weather_description*:** We observed redundancy between these two features, suggesting that one could be derived from the other to simplify the dataset.

5. **Weekday analysis:** Traffic volume varies throughout the week, with higher volumes observed on weekdays compared to weekends. Creating a categorical variable to capture this seasonality could enhance model performance.

   ![weekday_analysis](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/average_traffic_volume_by_day_of_the_week.png?raw=true)

6. **Analysis of new holiday data:** By examining the relationship between holidays and traffic volume, we discovered that not all holidays result in the same traffic patterns. Instead of creating a binary categorical variable, we propose creating an ordinal variable based on traffic volume distribution during holidays.

   **Example:**
   
   - For Christmas Day, the maximum traffic occurs between the 1st and 2nd quartiles, suggesting a value of 2 for this holiday.
   - For Independence Day and Christmas Eve, the peak traffic falls between the 2nd and 3rd quartiles, indicating a value of 3.
   
   ![holiday_analysis](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/max_traffic_volume_by_new_holiday.png?raw=true)

These insights provide a foundation for data cleaning, feature engineering, and model development to improve traffic volume prediction accuracy.

## Feature Engineering

During the feature engineering phase, we implemented several strategies to enhance the predictive power of our models:

1. **Temporal Features Extraction:** Extracted features such as day, month, year, weekday, and hour from the *date_time* feature to capture temporal patterns in traffic volume.

2. **Cyclical Transformation:** Applied sine and cosine transformations on the hour feature to encode the cyclical nature of traffic volume throughout the day, enabling our models to better understand hourly trends.

3. **Weekday Binary Variable:** Utilized insights from our EDA to create a binary variable indicating whether a day is a weekday or weekend. This categorical feature helps our models account for the varying traffic patterns between weekdays and weekends.

4. **Ordinal Holiday Variable:** Leveraged findings from our EDA to construct an ordinal variable representing the impact of holidays on traffic volume. This ordinal variable allows our models to differentiate between holidays based on their observed traffic volume patterns.

These feature engineering techniques serve to enrich the dataset with meaningful information, enabling our models to make more accurate predictions of traffic volume.

## Model Training and Evaluation

In this section, we trained and evaluated the performance of various machine learning models for traffic volume prediction. The following models were considered:

1. Linear Regression
2. Bayesian Linear Regression
3. Random Forest
4. XGBoost

### Results

The table below summarizes the results of our model evaluations:

| Experiment Name                                        | Test MSE       |
|-------------------------------------------------------|----------------|
| Exp 1 - Base Model - Linear Regression               | 11,82,175.334    |
| Exp 2 - Bayesian Ridge Linear Regression             | 11,81,813.387    |
| Exp 3 - Random Forest Regressor without Hyper Parameter Tuning | 1,32,295.172     |
| Exp 4 - XGBoost without Hyper Parameter Tuning       | 1,00,346.3723    |
| Exp 5 - XGBoost with Hyper Parameter Tuning          | 92,350.75562    |

With concerted efforts in data analysis, feature engineering, and model selection, we achieved remarkable results, leading us to secure a top position on the leaderboard in the hackathon.

![leader_board](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/leaderboard.png?raw=true)

## Implementation Details

### Technical Details
- **Programming Language:** Python
- **Packages Used:** sklearn, pandas, numpy, seaborn, xgboost
- **Code file:** [traffic-volume-prediction.ipynb](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/src/traffic-volume-prediction.ipynb)

## How to Run

The code is built on Google Colab on an iPython Notebook. 

```bash
Simply download the repository, upload the notebook and dataset on colab and update data path, and hit play!
```

## Contributors

I would like to acknowledge the following team members for their valuable contributions to this project:

- Sonti Roy
- Manoj David
