# Everlytics-MachineLearning

### Objective
Building a binary classification model that predicts if a website is real or phishing website given its features.

Building a Machine Learning model, from a higher level, require two things
  1.Data
  2.Learning Algorithm(Model)

## Data
### Preparation
Before applying ML models it is best to clean and understand data.
The transormation of data includes handling missing values, treating outliers, scaling, encoding variables, feature extraction, feature selection or sometimes even feature engineering.

### Missing Values
The data in this project does not have missing values.

### Feature Selection 
To select features for our model we use SelectPercentile class from sklearn.feature_selection module.
The f-statistic to calculate feature importance. 

![image](https://user-images.githubusercontent.com/51299040/175803176-fb21ca59-3801-463f-9abc-9713e4003f58.png)

Roughly 50% of our features show high importance. We can keep all the features but improvement in model shall be marginal and highly dispropotionate to the increase in computational expense.

### Feature Transformation
 All the features in the data are categorical in nature. Since there are no numerical features we apply only
**One Hot Encoding** to our data.

## Learning Algorithm
Before choosing the **best** learning algorithm, it is a good practice to have a baseline estimate of various ML algorithms using KFold cross validation and choose one 
for **Hyperparameter Tuning** using Grid Search Cross Validation for best performance. Metric used is F1 score.

### Logistic Regression
We use SGDClassifier with "loss" set to 'log' to create a Stochastic Gradient Descent based Logistic Regression implementation.

### Linear Support Vector Machine
We use SGDClassifier with "loss" set to 'hinge' to create a Stochastic Gradient Descent based Support Vector Machine implementation.

### RBF Kernel SVM
The data is not linearly separable. To create complex decision boundaries we try RBF Kernel SVM.

### Bernoulli Naive Bayes
Since the entire data in our transformed feature space is Sparse matrix of indicator vectors, we can apply Bernoully Naive Bayes classifier.

### Decision Tree Classifier
Since our data is not linearly separable and requires complex decision boundaries, DTC has the capacity to create very complex decision boundaries down to single data point.But * **With great representational capacity, comes great variance!** * DTC are very prone to overfitting if not regularized or pruned.

### Random Forest Classifier
To curb overfitting of single decision tree we use resort to collective wisdom, creating many short decision tress and using create a voting mechanism.

## Verdict
Random Forest Classifier gives best results. We tune the Hyperparameters of the model.
