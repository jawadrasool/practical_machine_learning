## Introduction
Using devices such as Jawbone Up, Nike FuelBand, and Fitbit it is now possible to collect a large amount of data about personal activity relatively inexpensively. These type of devices are part of the quantified self movement - a group of enthusiasts who take measurements about themselves regularly to improve their health, to find patterns in their behavior, or because they are tech geeks. One thing that people regularly do is quantify how much of a particular activity they do, but they rarely quantify how well they do it. 

Six participants had accelerometers on the belt, forearm, arm, and dumbell. They were asked to perform barbell lifts correctly and incorrectly in 5 different ways. In this project, the goal is to use data from these accelerometers and predict the manner in which they did the exercise (given in the "classe" variable in the training set). Using the prediction model, 20 different test cases are also predicted.

## Data used in this Project

The data for this project come from [HAR](http://groupware.les.inf.puc-rio.br/har), and a detaled description of their work is provided in "Velloso, E.; Bulling, A.; Gellersen, H.; Ugulino, W.; Fuks, H. **Qualitative Activity Recognition of Weight Lifting Exercises**, *Proceedings of 4th International Conference in Cooperation with SIGCHI (Augmented Human '13)*, Stuttgart, Germany: ACM SIGCHI, 2013." According to this paper, six male participants, aged between 20-28 years with little
weight lifting experience, were asked to perform one set of 10 repetitions
of the Unilateral Dumbbell Biceps Curl in five different fashions: 

- exactly according to the specification (Class A), 
- throwing the elbows to the front (Class B), 
- lifting the dumbbell only halfway (Class C), 
- lowering the dumbbell only halfway (Class D) and 
- throwing the hips to the front (Class E). 

Class A corresponds to the specified execution of the exercise, while the other 4 classes correspond to common mistakes.

### The dataset

Train data can be found at: [https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv](https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv)

Test data can be downloaded from [https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv](https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv)

We see that there are 19622 observations and 160 variables. The variable *classe* is what the models will try to predict. The test data, on which I'll use my prediction model to predict 20 different cases:

## Data Preparation

For data preparation, I removed the following variables from the dataset:

- Variabels that are for identification purposes only
- Variables with more than 80% of missing values
- Near zero variance variables

We are now left with 54 variables in our dataset. This number is still very high and use of PCA to reduce the number of variabels might not be a bad idea. However, I'll not use it in this project.

Now, I split the training dataset into training (70%) and validation set (30%). I'll use validation set for testing the performance of my models and selecting the best model.

## Modeling

We use three different models to predict the outcome. These models are decision tree, random forest and gradient boosting machine. 

#### Decision Tree

The accuracy is around 75%, which is not very high. The **out-of-sample error** is 25%. 

#### Random Forest

With random forest, we reach an accuracy of 99.7% using cross-validation with 3 steps. The **out-of-sample error** is thus 0.3% only. The performance of random forest is excellent, it seems.

#### Gradient Boosting Machine

With gradient boosting, we achieve an accuracy of 98.6% on the validation dataset. The **out-of-sample error** is thus 1.4% only. The gradient boosting model performed very close to the random forest model.

## Prediction on Test Data

Since the performance of the random forest model is the best among the three models, I used it to predict the values of *classe* variable for the test data containing 20 observations.
