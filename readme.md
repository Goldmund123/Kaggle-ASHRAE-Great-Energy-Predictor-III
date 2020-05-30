## DATA SOURCE

The American Society of Heating, Refrigerating, and Air-Conditioning Engineers (ASHRAE) posted a statistics competition on the Kaggle website (https://www.kaggle.com/c/ashrae-energy-prediction/data). The data comes from over 1,000 buildings with a three-year timeframe of metered building energy usage in fields of chilled water, electric, hot water, and steam meters. In order to perform better estimations of the energy-saving investments, large scale investors and financial institutions will be more inclined to invest in this area to enable progress in building efficiencies.


## DATA DESCRIPTION

There is a total of five different datasets involved in this project, including meta information of the buildings, energy usage records for the training set and test set, and weather data from the meteorological stations near the training set and test set. The finalized training and test sets are achieved by merge data files based on the identification numbers of the sites and the buildings. In general, there are 13 features and 1 outcome variable in this project. The features include:

1. time of the measurement was taken
2. meter ID code for each building
3. indicator of the primary category of activities for the building based on EnergyStar property type definitions
4. gross floor area of the building
5. year of the building first opened
6. number of floors of the building
7. air temperature in degree Celsius
8. portion of the sky covered in clouds, in Oktas
9. dew temperature in degree Celsius
10. perception depth within an hour in millimeters
11. sea level pressure in millibar/hectopascals
12. wind direction
13. wind speed at meters per second

The target variable is the energy consumption in a kilowatt-hour.


## Evaluation Metric
the evaluation metric is Root Mean Squared Logarithmic Error. The RMSLE is calculated as:
<p align="center">
<img src="https://render.githubusercontent.com/render/math?math=\epsilon = \sqrt{\frac{1}{n} \sum_{i=1}^n (\log(p_{i} \+ 1) - \log(a_{i} \+ 1))^2 }">
</p>
Where:

$\epsilon$ is the RMSLE value (score)
$n$ is the total number of observations in the (public/private) data set,
$p_i$ is the prediction of the target, and
$a_i$ is the actual target for i.
$log(x)$ is the natural logarithm of x
Note that not all rows will necessarily be scored.


## Data leakage problem
Many participants found the original data source and used them as a validation set when they built their models. However, using leaked data during the training can leads the model to overfit to the test set and not to represent real-world data. Therefore, I decided not to use any leaked data points to improve the leader board score.

## Overview of methodology
1. Filled missing hours
2. Imputed missing variables with interpolation and Multivariate Imputation by Chained Equations
3. Generated new variables based on the given data
4. Label Encoding
5. K-fold cross-validation
6. LightGBM with various regularizations, such as subsampling and early stopping 

## Result on the Leader Board
The best model's RMSLE score was 1.280 and it was top 10% among 3614 teams.


## Required Packages
Scikit-learn >= 0.23
Pandas
Numpy
meteocalc
plotly
matplotlib
LightGBM
