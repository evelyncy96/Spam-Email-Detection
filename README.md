# Spam-Email-Detection

- **Goal:** Build classification model to detect whether an email is spam or not
- **Data source:** <http://archive.ics.uci.edu/ml/datasets/Spambase>
- **Model:** Support Vector Classifier/ XGBoost/ LightGBM/ Deep Neural Network/ Decision Tree/ Logistic Regression

### In this project we consider two scenarios:
1. What is the best model **in terms of the overall prediction accuracy** and what's the best hyperparameter of that model?
2. What is the best model **in terms of the cost sensitive condition** and what's the best hyperparameter of that model?

### Process

- EDA
- Data Preprocessing
- Modeling 
  - **Nested CV:** Find the best model
  - **Hyperparameter tuning:** Find the best parameter
  - **DNN Tuning:** Kera tuner for DNN tuning
- Conclusion

### Conclusion

- For the first scenario, I first used Nested CV to find the best model among several classification models, such as **Decision Tree/ Logistic Regression/ LightGBM/ XGBoost/ Support Vector Classifier.** The result shows that XGBoost has the best performance. Therefore I conducted hyperparameter tuning to find the best parameter of XGBoost, the best parameter is {'estimator__colsample_bytree': 0.3, 'estimator__learning_rate': 0.01, 'estimator__max_depth': 3, 'estimator__n_estimators': 300, 'estimator__objective': 'binary'}. The accuracy of this model is 95.7% on training set and 94.6% on testing set. **I also built deep neural network and use kera-tuner to find the best number of layers, nodes and learning rate, and the accuracy of DNN model after tuning is 92.18%.** To sum up, I conclude that **XGBoost is the best model we found under the first scenario.** 

- For the second scenario, I repeated the process as I did in the previous scenario. I first used nested CV to find the best models among those same classification models and conducted hyperparameter tuning to find the best parameter of that specific model. The only difference is that I create a customized scoring function which takes the cost into account. The lowest cost model is LightGBM with parameter {'estimator__colsample_bytree': 0.3, 'estimator__learning_rate': 0.01, 'estimator__max_depth': 3, 'estimator__n_estimators': 300, 'estimator__objective': 'binary'}. I also draw the ROC curve and Lift Curve to show the performance of final model. To sum up, we conclude that **LightGBM is the best model in terms of the cost-sensitive scenario.**
