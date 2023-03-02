# Customer-Behavior-Prediction-Machine-Learning
<p align="center">
<img width="859" alt="Screen Shot 2023-03-02 at 1 03 14 AM" src="https://user-images.githubusercontent.com/61670089/222344573-10023848-f43c-47db-b150-7daceabc1c8f.png">
</p>

### Gradient Boosting
We first tried one of the Boosted Learners, Gradient Boosting. Based on HW4’s Gradient Boosting, solely making some adjustments for parameter selections did not offer a greater improvement, which remains around 0.695. So, we decided to implement the sklearn library, with the GradientBoostingClassifier function. For the parameters, we mainly adjusted learning_rate (default is 0.1) and n_estimators (default is 100). As the learning_rate is lower, the
training error will increase a little, but the validation error will be decreasing and the auc score will be higher. However, we don’t want the learning_rate to be too low, so they won’t efficiently learn from the training data. Thus, we want the learning_rate to be a bit lower than 0.1, so we set the parameter as 0.05. Due to the trade-off between these two parameters, as we decrease the number of the learning_rate, we need to increase the number of n_estimators. After cross comparing the auc score and the validation error for 100, 150, 200, 250, and 300, we found out it is higher when n_estimator is 300, and the learning_rate is 0.05. The auc for this learner is 0.721. This learner from sklearn library has an increase from what we had in HW4.

The next parameter we changed was the number of features we selected. The original number we set was 50 which was so large that the diversity of the learners would decrease. When the diversity was too low, we might fail to reach the random condition for those learners. After a series of testing, we chose the subset of 25 features since we also did not want the number of features so small that there were insufficient features to train the model effectively and the bias might be really high. Thus, we decided to choose 25 as the number of features we selected and the Kaggle score is 0.734 which improved a lot.

### Random Forest
The next model we tried is the Random Forest. We employed the tree classifiers in the
mltools. We only kept the first 41 features, which are numeric, like we did in HW 4. Then, we did not add any restriction or new features on the data. We splitted the training data and the validation data with ratio 0.65 (65% training data). To avoid overfitting, we didn’t set the ratio too high. Based on the Random Forest in HW 4, we revised the model through changing some parameters. We first changed the ensemble size from 25 to 30, but there seemed no great decrease in the validation error. The validation score changed from 0.36 to 0.35. The Kaggle score for test data was still 0.709 which almost remained the same as our previous one in HW 4.

### Decision Tree
Not only did we try new models, We also refined the decision tree model from HW4. With previous experiments, we made a decision tree learner with maxDepth of 9 and minParent of 2^9. Moreover, after testing the training and Validation AUC, we used the whole dataset to train the learner and got a good Kaggle score.

### Weighted Ensemble
In order to make the best use of all the models we learned above, we did an ensemble model which embedded the best three models we trained above (Gradient Boosting, Random Forest, and Decision Tree). We first tried to simply add up the predictions in each of the three models and then divided by 3 to get the ensembled prediction. Further trying to eliminate the influence of the bad predictor in these three models, we calculated the prediction with weights. The two predictions with closer distance between them will have a weight of 1.2 and the prediction left far away will have a weight of 0.6.

### Conclusion
Based on the table we listed on the top, the ensemble model has a relatively higher AUC score among those models since it combines three different models and chooses the best in prediction.What is predicted wrong in one model may be predicted correctly in the others. Thus, the Kaggle score for the ensemble is the highest.
Since the Random Forest has more randomness, and it has multiple random subsets so it could find the best feature to implement. This is why Random Forest works relatively well.
Neural Network works poorly since we are not able to batch the data and thus lead the model extremely easy to fall on to local minimums while gradient.

