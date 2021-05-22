# Starbucks_Capstone_Challenge
#ayman metwally

### Table of Contents

1. [Project Overview](#overview)
2. [Problem Statement/Metrics](#Problem)
3. [Project Components](#components)
4. [Installation](#installation)
5. [Motivation](#Motivation)
6. [File Descriptions](#files)
7. [Instructions](#instructions)
8. [Summary](#Summary)
9. [Acknowledgements](#Acknowledgements)

## Project Overview<a name="overview"></a>

Customer satisfaction drives business success, and data analytics provides insight into what customers think. Each person has some hidden traits that make the people act differently to offers while a few converts to sales. Since marketing is a cost, business likes to study how each segment of customer responds to different offers and how they can target/tailor the offer to the individual to improve RoI by converting a potential customer to a smiling customer.
The Starbucks Udacity Data Scientist Nanodegree Capstone challenge data set is a simulation of customer behaviour on the Starbucks rewards mobile application. Periodically, Starbucks sends offers to users that may be an advertisement, discount, or buy one get on free (BOGO). An essential characteristic regarding this dataset is that not all users receive the same offer.
This data set contains three files. The first file describes the characteristics of each offer, including its duration and the amount a customer needs to spend to complete it (difficulty). The second file contains customer demographic data, including their age, gender, income, and when they created an account on the Starbucks rewards mobile application. The third file describes customer purchases and when they received, viewed, and completed an offer. An offer is only successful when a customer both considers an offer and meets or exceeds its difficulty within the offer's duration.

## Problem Statement / Metrics<a name="Problem Statement / Metrics"></a>

he problem that I chose to solve is to build a model that predicts whether a customer will respond to an offer. My strategy for solving this problem has the following steps. 
1- clean and combine offer portfolio, customer profile, and transaction data. Each row of this combined dataset will describe an offer's attributes, customer demographic data, and whether the offer was successful. 
2- apply a different machine learning model and assess additional accuracy and F1-score. The 'naive model' assumes all offers were successful. This provides me with a baseline for evaluating the performance of models that I construct. Accuracy measures how well a model correctly predicts whether an offer is successful. However, if the percentage of successful or unsuccessful offers is deficient, accuracy is not a good measure of model performance. For this situation, evaluating a model's precision and recall provides better insight into its account. Hence, I chose the F1-score metric because it is "a weighted average of the precision and recall metrics". 
3-, compare the performance of logistic regression, random forest, and gradient boosting models. 
And finally, refine the parameters of the model that has the highest accuracy and F1-score.

## Project Components<a name="components"></a>

The entire analysis would contain below steps:

1. Analyse each of the portfolio, profile and transaction data.
2. Clean and transform each of the portfolio, profile and transaction data.
3. Combine portfolio, profile and transaction data.
4. Select a performance metric to analyse performance of the model and to compare different models.
5. Compute the performance of a baseline model against which performance of other different models would be compared.
6. Select best performing model based on the metric and training time.
7. Calculate the feature importances given by best estimator of the trained model.
8. Compute the performance of best model on test set and visualize the performance via confusion matrix plot.

## Installation <a name="Installation"></a>

In order to be able to execute your own python statements it should be noted that scripts are only tested on anaconda distribution 4.5 in combination with python 3.8 or above. The scripts don't require additional python libraries.
Python Libraries used are as follows>
Progressbar
joblib 
Pandas
Numpy
Matplotlib
Seaborn
sklearn (train_test_split, RandomizedSearchCV, GridSearchCV, MinMaxScaler, accuracy_score, f1_score, fbeta_score, make_scorer, LogisticRegression, GradientBoostingClassifier, RandomForestClassifier)

## Motivation<a name="Motivation"></a>
This project is done as part Udacity Data Scientist Nanodegree program - Starbucks Capstone challenge, this is a final project submission of my certification.

The data is contained in three files:

* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer 
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record

## Instructions<a name="instructions"></a>

1. The entire anlaysis is contained within the jupyter notebook.
2. All 3 .json files should be located in data folder as combined data would be created from these 3 files located in data folder.


## Summary<a name="Summary"></a>
 Summary of the results of the analysis
Visualization and Linear regression are used in the analysis and get the conclusion:
> Advertising can help increase revenues but not profits necessarily. Informational offer has more negligible effect than BOGO and discount. However, if Starbucks intend to attract more consumers, promotion costs might offset incomes while there is not enough customer response.
> Due to the low response rate, it suggests that advertising higher income females who are three years member seem a good idea since they are most likely spending more in Starbucks.
* Offer_id 'fafdcd668e3743c1bb461111dcafc2a4' is the most successful offer and corresponds to 'discount' offer with minimum spend of 10 dollars within 10 days of receiving of the offer and having reward of 2 dollars. Offer_id '3f207df678b143eea3cee63160fa8bed' is the least successful offer and corresponds to informational offer with no minimum spend required having no reward.

* All our trained classifier produce better f1_score than the baseline model's f1_score of 0.6996. RandomForestClassifier and GradientBoostingClassifier got nearly equal f1_score(approx. 0.92) but RandomForestClassifier took very less time to train than the GradientBoostingClassifier. Therefore, best performing classifier algorithm among the above 4 classifiers was RandomForestClassifier.

* The hyperparameters of the trained RandomForestClassifier was further fine tuned using GridSearchCV and our model got improved and produced a better f1_score of 0.9319 with cross-validation.

* Our best estimator produced f1_score of 0.9336 on test data, which is quite good.

* Top 10 features which influence whether the customer will respond to an offer or not after viewing the offer are: 'total_amount', 'membership_tenure' , 'social', 'difficulty', 'duration', 'reward', '2018', '2016', 'income_30ths' and 'age_50s'.


*Starbucks, periodically send the offers to users that may be an advertisement, discount or buy one get one free offer this data set is a simulation of customer behavior on the Starbucks rewards mobile application. An important characteristic of this dataset is that not all users receive the same offer. Hence, identifying the right individuals for targeted marketing who will respond positively to an offer Machine Learning Model used as part of the project Logistic Regression Model random forest gradient boosting naive predictor This model will be compared to the highest training data accuracy and F1-score. Bias and variance are two characteristics of a machine learning model. Bias refers to inherent model assumptions regarding the decision boundary between different classes. On the other hand, variance refers to a model’s sensitivity to changes in its inputs. Both random forest and gradient boosting models are a combination of multiple decision trees. A random forest classifier randomly samples the training data with replacement to construct a set of decision trees that are combined using majority voting. In contrast, gradient boosting iteratively constructs a set of decision trees with the goal of reducing the number of misclassified training data samples from the previous iteration. A consequence of these model construction strategies is that the depth of decision trees generated during random forest model training is typically greater than gradient boosting weak learner depth to minimize model variance. Typically, gradient boosting performs better than a random forest classifier. However, gradient boosting may overfit the training data and requires additional effort to tune. A random forest classifier is less prone to overfitting because it constructs decision trees from random training data samples. Also, a random forest classifier’s hyperparameters are easier to optimize. Random Forest model was the best model on training dataset hence best fit parameters were refined further to test on 'test dataset', the performance of the model accuracy and F1-score improved as compared with training set and overfitting signs were observed.

* [Project Notebook: Starbucks Capstone Challenge]()
* [Blog Post: Who will engage in Starbucks Offers?](https://ayman-metwally.medium.com/starbucks-capstone-challenge-28922fa03cae)


### Acknowledgements

This project was completed as part of the [Udacity Data Scince Nanodegree](https://classroom.udacity.com/nanodegrees/nd025/dashboard/overview. The dataset used in this project contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. [Starbucks® Rewards program: Starbucks Coffee Company](https://www.starbucks.com/rewards/).
Medium links:

