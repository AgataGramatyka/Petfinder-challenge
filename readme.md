# Petfinder challenge: predicting pet adoption speed

## Introduction
The featured notebook focuses on data from an ongoing Kaggle competition, details available [here] (https://www.kaggle.com/c/petfinder-adoption-prediction). The objective is to develop algorithms to predict the the speed at which a pet is adopted, based on the pet’s listing on Petfinder, a Malaysian website for pet adoptions.

The tabular data provided includes close to 15,000 listings and the following variables:
* Age
* Breed
* Colour
* Gender
* Size at maturity
* Fur length
* Whether the animal was sterilized, dewormed and vaccinated
* Health
* Pet description
* The target variable adoption speed, ranging from 0 (adopted on the very same day) and 4 (not adopted)

On top of that, Petfinder provides photos of the pets and image metadata in json format obtained by running the images through Google's Vision API.

## Data preparation
The train.csv file is the principal source of data, with feature labels and image metadata available in additional files. In order to synthetise a comprehensive DatFrame for further analysis, I have taken the following steps:
1) Added Colour, Breed and State labels to replace IDs
2) Incorporated the image metadata including image description and score
3) Divided pets into pure and mixed breed which will help simplify the model
4) Remove outliers and missing values
5) Create dummy variables for categorical variables


## Machine learning
First of all, I have prepared the data for modelling by splitting it into train and test datasets, standardising it using Scikit-learn's StandardScaler and finally, ranking the different features with Scikit-learn's tool RFECV. The result shows that all variables are relevant to the model, they will therefore be retained and fed into the Machine Learning algorithms.

Because we are dealing with a multi-class classification task, careful choice of algorithm is very important as not all classifiers are well adapted to this type of problem. I have selected Random Forest, Multinomial Naive Bayes and K-Nearest Neighbours, which I then aggregated in an ensemble model using VotingClassifier.

For performance gains, I have also applied the AdaBoost and Gradient Boosting algorithms.

## Results
With a maximum test score of 38%, the results so far are underwhelming. Further analysis is needed to improve the prediction, and my intuition tells me that applying Neural Networks to the photos could work much better.

I will work on this next, so watch this space!
