# Flipr-ML-Hackathon-7.0

This repository contains my submission for Flipr Hackathon 7.0 for the Machine Learning Task. The following are the information about the files contained in this repository:

1. Data.xlsx file contains train dataset on which model has to be trained, which contains parameters of IPL 2018 and total runs in the IPL 2019. It also contains test dataset, which contains parameters of IPL 2019, using which the total runs in IPL 2020 needs to be predicted.

2. Variable_Description.xlsx file contains the description of the various columns present in the data file.

3. Hackathon_7.0_ML_Guidelines.pdf contains the problem statement, objective of the problem statement and it also presents the context of the problem.

4. Flipr_Hackathon_7_0_Machine_Learning_Task_16_10_2020.ipynb file contains the main code.

5. Data_final_answer_flipr.xlsx is the final predicted output file having the names of the 100 players and the predicted total runs scored by them in IPL season 2020.

6. Solution_Sheet.pdf file contains the explaination of the model used here for prediction.


## Description of the process followed in order to accomplish this task


# Given:

The dataset given contains the following:

Train set: IPL 2018 statistics along with the total runs scored in IPL 2019 of 100 players.

Test set: IPL 2019 statistics of 100 players.

# Objective:

The objective of the problem statement is to predict the total runs scored by each of the given player in IPL 2020. The output file should contain the player name and the total runs scored.


# Procedure followed:

1. Hypothesis Formation - To predict the total runs scored by each player in the IPL season 2020 using a predictive machine learning model which would be trained on IPL 2018 statistics and tested on IPL 2019 statistics to predict IPL 2020 runs. From the problem statement it was understood that the problem was a regression problem.

2. Importing data from the provided excel file as two pandas dataframe (df1 and df2).

3. Data Exploration steps were performed which showed that there were no null values present explicitly in the given dataset but there were two columns which had "*" and "-" in them beacuse of which they were treated as objects and not int or float. Also the different feature columns varied in ranges.

4. Then the train data set was split into the feature(X) and target(y) columns. The test set contained only the target columns. The above mentioned special characters were removed and "None" was inserted as null values inplace of them. After this only three null values were found in the batting average feature column and this was filled with the value of the previous Highest Run scored column.

5. Data Transformation steps were performed. To address the issue of varied ranges in the different columns the data was standardized using Standard Scaler module and normalized using the MinMaxScaler module but later proceeded with standardized data because the density and the pair plot showed gaussian distribution.

6. Then again the data exploration part was done using the standardized data through plots like line plot, box plot, density plot and pair plot. No much outliers were observed in the data using the box plot. Density plot and pair plot majorly showed that the data follows gaussian distribution.

7. Then the train set was divided into train and validation set which comprised of 20% of the train set.

8. Then the model building steps were performed. Different models were trained on the training dataset and validated on the validation set. Regression based metrics were to compare the result.

9. The different models build are - Linear Regression, Lasso Regression, Ridge Regression, Bayesian Ridge Regression, Elastic Net CV, Stochastic Gradient Descent (SGD), Decision Tree, Random Forest, Ada Boost, Gradient Boosting, Extra Trees Regression, Extra Gradient Boosting, Support Vector Regressor (SVR), and finally Artificial Neural Network.

10. The different regression metrics used here were - Explained Variance Score, Mean Absolute Error, Mean Squared Error, Root Mean Squared Error, Mean Squared Log Error, r squared Score, Adjusted r squared Score and the cross val score obtained from the Repeated K-Fold cross validation.

11. When the values of different metrics were compared, Extra Gradient Boosting (xg boost) performed the best. It had the mean highest cross-validation score (0.99 (+/- 0.1)) (here k was taken as 10 and the repeats were taken as 3), the highest adjusted r squared score (approx 0.991764) and lowest root mean squared error value (approx 8.9302). Hyperparameter tuning was also performed but that did not show much improvement in performance. Feature selection was also done but that also did not show much improvement in performance. For the above result xgboost was chosen as the model of choice. The performance of the various model according the decreasing value of adjusted r square is XGBoost> Extra Trees> Random Forest> Gradient Boosting> Ada Boost> SVR> SGD> Ridge Regression> Bayesian Ridge Regression> Linear Regression> Elastic Net CV> Decision Tree> Lasso Regression.

12. Repeated K-fold cross validation was performed on xg boost model to check for any over-fitting issue. K was here taken as 5 and the number of repeats were taken as 3. The model performed equally well for all the iterations.

13. XGBoost was used for the final prediction of IPL 2020 total runs scored by each player from the given test set and was exported and saved as the final output excel file. 

All the steps have been indicated in the code as comments.


# Result Obtained:

XGBoost performed the best among all the other models build, with the highest value of cross-validation and the adjusted r square score and the lowest error values (mean square, root mean square and mean absolute error). It was chosen as the model of choice to predict IPL 2020 runs and the final output file containing the names of the player and the predicted runs were generated.
