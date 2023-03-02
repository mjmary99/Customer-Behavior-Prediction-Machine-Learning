# Customer-Behavior-Prediction-Machine-Learning
<p align="center">
<img width="859" alt="Screen Shot 2023-03-02 at 1 03 14 AM" src="https://user-images.githubusercontent.com/61670089/222344573-10023848-f43c-47db-b150-7daceabc1c8f.png">
</p>

### Gradient Boosting
We first tried one of the Boosted Learners, Gradient Boosting. Based on HW4’s Gradient Boosting, solely making some adjustments for parameter selections did not offer a greater improvement, which remains around 0.695. So, we decided to implement the sklearn library, with the GradientBoostingClassifier function. For the parameters, we mainly adjusted learning_rate (default is 0.1) and n_estimators (default is 100). As the learning_rate is lower, the
training error will increase a little, but the validation error will be decreasing and the auc score will be higher. However, we don’t want the learning_rate to be too low, so they won’t efficiently learn from the training data. Thus, we want the learning_rate to be a bit lower than 0.1, so we set the parameter as 0.05. Due to the trade-off between these two parameters, as we decrease the number of the learning_rate, we need to increase the number of n_estimators. After cross comparing the auc score and the validation error for 100, 150, 200, 250, and 300, we found out it is higher when n_estimator is 300, and the learning_rate is 0.05. The auc for this learner is 0.721. This learner from sklearn library has an increase from what we had in HW4.

### Random Forest
The next model we tried is the Random Forest. We employed the tree classifiers in the
mltools. We only kept the first 41 features, which are numeric, like we did in HW 4. Then, we did not add any restriction or new features on the data. We splitted the training data and the validation data with ratio 0.65 (65% training data). To avoid overfitting, we didn’t set the ratio too high. Based on the Random Forest in HW 4, we revised the model through changing some parameters. We first changed the ensemble size from 25 to 30, but there seemed no great
decrease in the validation error. The validation score changed from 0.36 to 0.35. The Kaggle score for test data was still 0.709 which almost remained the same as our previous one in HW 4.
