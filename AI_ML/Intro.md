# A Gentle Introduction to Machine Learning: Concept Notes

## 1. The Core Purpose of Machine Learning

 -  At its foundation, machine learning is entirely focused on making predictions and classifications based on data.

 -  Examples include predicting how fast someone runs based on their diet or classifying whether a person will like a specific video channel based on their interests.

## 2. Training Data vs. Testing Data

 -  Training Data: This is the original dataset used to build or "fit" the machine learning model.

 -  Testing Data: This consists of new, unseen data points used to evaluate the model's accuracy. The ultimate test of any machine learning method is how well it performs with testing data, not training data.

## 3. Model Evaluation and The Bias-Variance Tradeoff

 -  A model that is highly complex (like a squiggly line) might fit the training data perfectly, while a simpler model (like a straight line) might not fit the training data as closely.

 -  To decide which model is better, you measure the distance between the actual results in the testing data and the predictions made by each model. The model with the smallest sum of distances is the better choice for real-world predictions.

 -  Bias-Variance Tradeoff: This is the phenomenon where a machine learning method fits the training data extremely well but fails to make accurate predictions on new testing data.

## 4. Decision Trees

 -  A decision tree is a simple machine learning classification method that makes predictions by running data points through a series of yes/no questions.

 -  Like all machine learning models, a decision tree is built using training data and its accuracy must be verified by running testing data through its branches to see if the predictions match reality.

 ----

 # The Purpose of Cross-Validation

 When building a predictive model, you have to choose between many different machine learning methods (like Logistic Regression, K-Nearest Neighbors, or Support Vector Machines). Cross-validation allows you to compare these different methods and evaluate how well they will perform in practice on unseen data.

 ## How Cross-Validation Works
 
 Instead of just splitting the data once (e.g., 75% for training, 25% for testing), cross-validation divides the data into multiple blocks and tests them all systematically:

1. The data is divided into equal-sized blocks.
 
2. The algorithm is trained on all but one of the blocks.
 
3. The remaining block is used to test the method, and the performance is recorded.
 
4. This process repeats until every single block has been used as the testing data exactly once.
 
5. The results are summarized at the end to see which machine learning method performed the best.

## Types of Cross-Validation

-  K-Fold Cross Validation: Dividing the data into an arbitrary number of "K" blocks. For example, dividing the data into 4 blocks is called "4-Fold Cross-Validation". In practice, 10-Fold Cross-Validation is the most common standard.

- Leave-One-Out Cross Validation: An extreme version where every single individual patient or data sample is treated as its own block and tested individually.
