<h1> Forest Fires Prediction with Regression (Log Transformation - 1st Approach) </h1>

This dataset was collected from UCI Machine Learning Repository and consists of 517 records (rows) and 13 features(columns).
Dataset and attribute Information can be found in info.md file in the main folder.

The output variable 'area' is very skewed towards 0.0 (consists lots of zeroes as well) and hence we need to consider that when building our model. Here we will be applying log(1+x) transformation. <br>

The data analysis is divided into 3 parts/files. The first part covers data wrangling and EDA, the second parts consists of scaling and modelling and in the last part we will be building our pipeline that will simplify our model deployment in the end.


* <h3> Data Wrangling and EDA - </h3>
Forest_Fires_Wrangling.ipynb file refers to the first part and shows step by step with comments on how to perform Exploratory Data Analysis(EDA). Various techniques will be performed such as "Log(1+x) Transformation", "Plotting(Boxplots, Histograms)", Cyclical Encoding etc.

Note: To prevent data leakage we usually split the file into train and test sets before performing any EDA, preprocessing and modelling. Here our outcome variable is highly skewed and consists of lots of zeroes, so we have used the approach of stratified split for conitnuous variables by discretizing(binning) the outcome variable 'area'. To get a better understanding, have a look at the code and comments.

* <h3> Scaling and  Modelling - </h3>
Forest_Fires_Modelling.ipynb file refers to the second part. Here we’d like to examine the impact of the input variables, so we will be testing two distinct feature selection setups. The two feature selection setups are as follows:-
1) STMFWI using spatial, temporal, the four FWI components and the 3 weather variables (RH, wind, temp)
2) FWI with the four FWI components (FFMC , DMC, DC, ISI)

We will be scaling using Robust Scaler since our data consists of outliers. </n>
We will first try to fit a simple linear regression model and assess its performance using R square (R2) metric.
We will then 3 try non-linear regression models - SVR (SVR) Gaussian with rbf kernel, Random Forest (RF) and Gradient Boosting (GB)

Metrics:- We will use Mean Absolute Deviation Error (MAD) as primary metric and Root Mean Squared Error (RMSE) as secondary metric to assess our non linear models. In both metrics, lower values result in better predictive models. However, note that the RMSE is more sensitive to high errors (outliers).
We will also use the Regression Error Characteristic (REC) curve to compare our models, which plots the error tolerance (x-axis), given in terms of the absolute deviation, versus accuracy i.e. the percentage of points predicted within the tolerance (y-axis). The REC curve is used to compare the predictive ability of fitted models. The ideal regressor should present a REC area close to 1.0 

We will train our model using ‘Grid Search’ and try to find the most optimal parameters for our model. Here, we have applied a 5-fold cross validation with 3 replications in our Grid Search’ to each configuration to assess the predictive performances.  

We will also use permutation_importance function from sklearn to check our most important features given by our different models on train and test sets.

Lastly, we will save our model using sklearn joblib function so that we can use it later when building pipeline.

Note 1: That R-squared for nonlinear models cannot be used because the research literature shows that it is an invalid goodness-of-fit statistic for this type of model. There are bad consequences if you use it in this context. The reason being in nonlinear regression, SS Regression + SS Error do not equal SS Total which completely invalidates R-squared for nonlinear models, and it no longer has to be between 0 and 100%.

Note 2: Here we have defined a function to calculate the error tolerance (in terms of the absolute deviation) and accuracy (percentage of points predicted within the tolerance), so that we can compare our models using the REC curve.
Link for the research paper on REC curve by Jinbo Bi and Kristin P. Bennett :-
* http://homepages.rpi.edu/~bennek/papers/rec.pdf

* <h3> Building Pipelines - </h3>
Forest_Fires_Pipelines.ipynb file refers to the 3rd part. Here we demonstrate step by step with comments how to build pipeline using sklearn to simplify our model deployment for our first setup  i.e. STMFWI using our best model with most optimum parameters and predicting the outcome variable. Here we will demonstrate how to build custom transformers (for custom function/operations) that can be fitted to our pipeline and usage of columns transformer. 
