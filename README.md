
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
- Duplicates at *date_time* level
- *holiday* data is not mapped correctly
- Data has cyclical nature based on hours
![date_time_analysis_with_traffic_volume](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/traffic_volume_by_datetime.png?raw=true)
- *weather_main* and *weather_description* can derive from each other
- Weekday analysis: We can observe that traffic is more on weekdays compared to weekend.
If we create categorical variable around it, it can help model to understand this seasonality.
![weekday_analysis](github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/average_traffic_volume_by_day_of_the_week.png?raw=true)
- Analysing new holiday data : By observing below plot,we can say that we don't get same spikes traffic volume for every holiday.
Instead of creating binary categorical variable, we can create ordinal variable using holiday data.

**Example:**

For Christmas Day, We are getting max traffic in between 1st and 2nd quartile so we can give value as 2

For Independance day and Christmas Eve, We are getting max traffic in between 2nd and 3rd quartile so we can give value as 3
![holiday_analysis](https://github.com/vishawjeetd/Traffic-Volume-Predictor/blob/main/img/max_traffic_volume_by_new_holiday.png?raw=true)



