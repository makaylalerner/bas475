# Predictive Analytics in R

Skills: Data Analysis, Data Visualization, Machine Learning, R
Brief Summary: Testing multiple time series models to predict the amount of questions submitted by users
GitHub: https://github.com/makaylalerner/bas475

# Stack Overflow Question Counts Prediction Competition

Prepared for BAS 475 by Makayla Lerner and team of peers 

## Objectives and Techniques

The objective of this project is to find the prediction model with the lowest Root Mean Square Error (RMSE) to ensure accuracy. The models and techniques we investigated are the Autoregressive Integrated Moving Average (ARIMA) which uses past values to predict future values and Exponential Smoothing which helps to interpret trends and seasonal components of the data. 

## Historical Data Aggregation

- The data presented for Python and R questions asked through the Stack Overflow website were in csv files
- Each of the csv files were manipulated to show the dates as month and year in one column and the count of questions in another. These files were merged on an inner join to have as many match up dates for accurate comparisons and forecasting.
- One aspect that had to be agreed on was how to fill the missing data from October 2008 in the R data. It was decided to fill the data down using the previous month’s, September 2008’s, value
- Once this was established we transformed the data into a data frame that could be used for model creation and analysis.

## Initial Assessments

![Untitled](Predictive%20Analytics%20in%20R%20d2c1f6284d0a4fd6aa00669da58bd62b/Untitled.png)

- This graph shows the autoplot for our raw data
    - From this we can see that there is a clear trend, seasonality, and variation in that seasonality over time.
    - Due to the variation, we established that the box cox method would be involved in models that would accept it.
    - Any models that would allow for seasonality and trend to be taken into account would be assessed.
    

## Selecting Models

- After running various models, narrowed down to two
- Models were evaluated based on accuracy
- Validated by comparing historical data with predictions

## Runner-Up: ARIMA Model

- ARIMA is a statistical model that uses past values to predict future values
- Parameters were adjusted to minimize error
- Optimal model:
    - Looked back two months in time
    - Adjusted for seasonal changes
    - Had second lowest typical miss among all models tested
    

![Untitled](Predictive%20Analytics%20in%20R%20d2c1f6284d0a4fd6aa00669da58bd62b/Untitled%201.png)

![Untitled](Predictive%20Analytics%20in%20R%20d2c1f6284d0a4fd6aa00669da58bd62b/Untitled%202.png)

## Best: Exponential Smoothing Method

- The model created using the Exponential Smoothing method places the most emphasis on the most recent observation and places less and less emphasis on the observations as they get farther from the most recent observation
- Like the ARIMA model, parameters were adjusted to minimize error

![Untitled](Predictive%20Analytics%20in%20R%20d2c1f6284d0a4fd6aa00669da58bd62b/Untitled%203.png)

## Predictions

Based on our model created from the Exponential Smoothing method, the table on the right shows our predictions for each month.

## ARIMA Residuals

- After eliminating trends and seasonal changes, the optimal model shows only random, non-correlated points with an expected outlier
- Meaning we accounted for nearly everything that could throw off the prediction

![Untitled](Predictive%20Analytics%20in%20R%20d2c1f6284d0a4fd6aa00669da58bd62b/Untitled%204.png)

## Exponential Smoothing Reasoning

- This model had the lowest RMSE (average miss the model makes) out of all created models
- The residuals plot (the plot on the top) and the acf plot (the plot on the bottom left) show no obvious patterns which means that our model has captured them from our data

| 2021 Nov | 24017 |
| --- | --- |
| 2021 Dec | 22220 |
| 2022 Jan | 23848 |
| 2022 Feb | 23982 |
| 2022 Mar | 26119 |
| 2022 Apr | 25602 |
| 2022 May | 25403 |
| 2022 Jun | 24686 |
| 2022 Jul | 25594 |
| 2022 Aug | 24402 |
| 2022 Sep | 23242 |
| 2022 Oct | 24896 |