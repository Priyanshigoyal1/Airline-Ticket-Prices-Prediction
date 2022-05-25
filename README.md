# Airline-Ticket-Prices-Prediction
Flight ticket prices can be something hard to guess, today we might see a price, check out the price of the same flight tomorrow, it will be a different story. In this project predicts the price of flight tickets.

ABOUT DATASET:
We have given a dataset of flight ticket prices which is of shape (10683, 11). In this
problem we have to predict the price of a flight ticket.
IMPORTING DATASET:
Given file is in the form of an excel file so we have to use pandas read_excel to load the
data. After loading it is important to check the complete information of data as it can
indicate much of the hidden information such as null values in a column or a row. There
is one NA value which we drop it.
Describe data which can give statistical analysis of it.

EXPLORATORY DATA ANALYSIS:

1. From description we can see that Date_of_Journey is a object data type,\
Therefore, we have to convert this datatype into timestamp so as to use this
column properly for prediction. For this we require pandas to_datetime to convert
object data type to datetime dtype.
.dt.day method will extract only day of that date**\ **.dt.month method will
extract only month of that date
Extracting Day AND Extracting month from the column Date_of_Journey

Since we have converted Date_of_Journey column into integers, Now we can
drop as it is of no use.
2. Departure time is when a plane leaves the gate. Similar to Date_of_Journey we
can extract values from Dep_Time.
Extracting hour AND Extracting minutes from the column Dep_Time
Now we can drop Dep_Time as it is of no use
3. Duration is the difference of dep time and arrival time. Extract minutes and hours
from the durations. Then add new two columns duration_hours and
duration_mins list to dataframe.

HANDLING CATEGORICAL DATA:
NOMINAL DATA: Nominal data is data that can be labeled or classified into mutually
exclusive categories within a variable. These categories cannot be ordered in a
meaningful way. For handle such data we used OneHotEncoder.
In this dataset Nominal data are:
1. Airline
2. Source
3. Destinations
4. Additional_Info
ORDINAL DATA: In statistics, ordinal data are the type of data in which the values
follow a natural order. One of the most notable features of ordinal data is that the
differences between the data values cannot be determined or are meaningless. For
handle such data we used LabelEncoder.
In this dataset Ordinal data is:

1. Total_stops

OneHotEncoding:
Performing OneHotEncoding on these above Nominal Data.

Airline Vs Price Graph

In this graph we can clearly see that Jet Airways Business has the highest Price. Apart
from the first Airline almost all are having similar median

Source Vs Price Graph

Almost similar median.
● Route and Total_Stops are related to each other.Therefore drop the Route.

Additional_info Vs Price Graph

From Additional_Info extract the ‘No check-in baggage included’ and ‘In-flight meal not
included’. Then drop the Additional_Info column and add two new columns ‘No check-in
baggage included’ and ‘In-flight meal not included’.

LabelEncoding:
As this is case of Ordinal Categorical type we perform LabelEncoder.
Perform LabelEncoding on the Total_stops "non-stop": 0, "1 stop": 1, "2 stops": 2, "3
stops": 3, "4 stops": 4 .

FEATURES SELECTION:

Finding out the best feature which will contribute and have good relation with target
variable. Following are some of the feature selection methods,
heatmap
feature_importance_
SelectKBest
CORRELATION MATRIX: Statisticians and data analysts measure correlation of two
numerical variables to find an insight about their relationships. On a dataset with many
attributes, the set of correlation values between pairs of its attributes form a matrix
which is called a correlation matrix.
Finds correlation between Independent and dependent attributes.

Here, we can see that the variables depend on each other.
1. Total stops have a highly positive correlation with prices.
2. By observing this we can select the features which are highly correlated.

ExtraTreeRegressor:
To perform feature selection using ExtraTreeRegressor, during the construction of the
forest, for each feature, the normalized total reduction in the mathematical criteria used
in the decision of feature split (Gini Index if the Gini Index is used in the construction of
the forest) is computed. This value is called the Gini Importance of the feature. To
perform feature selection, each feature is ordered in descending order according to the
Gini Importance of each feature and the user selects the top k features according to
his/her choice.
For this dataset Important feature Graph:

Here, we can see that Total_stops is one of the important feature which affect prices
highly as we also see it in the heat map.

FITTING MODELS :

This is the regression problem so I applied regression models in this dataset.
1. RandomForestRegressor:
Using RandomForestRegressor using sklearn library.
● R^2 score on train dataset: 0.9770633013293992
● R^2 score on test dataset: 0.8620968227604909
● MAE: 804.3463478047694
● MSE: 2813352.593918533
● RMSE: 1677.3051582578923
Visualize the y_test and y_pred graph.

2. XgBoost:
Using XgBoost using sklearn library.
● R^2 score on train dataset:0.963060144809135
● R^2 score on test dataset:0.8936472104393411
● MAE: 866.5499163218482
● MSE: 2169695.4513331465
● RMSE: 1472.988612085357
Visualize the y_test and y_pred graph.

3. LightGBM Regressor:
Using LightGBM using sklearn library.
● R^2 score on train dataset:0.8992678740590899
● R^2 score on test dataset: 0.8641622806709836
● MAE: 866.5499163218482
● MSE: 2169695.4513331465
● RMSE: 1472.988612085357
Visualize the y_test and y_pred graph.
