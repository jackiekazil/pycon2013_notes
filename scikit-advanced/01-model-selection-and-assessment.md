01 - Model Selection and Assessment

# Notes: Model Selection and Assessment

## Overview
- Model performance evaluation and **detection of overfitting with Cross-Validation**
- **Hyper parameter tuning** and model selection with Grid Search
- Error analysis with **learning curves** and the **Bias-Variance trade-off**
- Overfitting via Model Selection and the **Development / Evaluation set split**

## Optical Recognition of Handwritten Digits Data Set
- All images are 8x8 pixels
- 5620 samples
- 64 features

Split the dataset into 2 values - X, y    
data shape: (1797, 64), target shape: (1797,)     
classes: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]    

n_samples=1797
n_features=64

Let's visualize the dataset on a 2D plane using a projection on the first 2 axis extracted by Principal Component Analysis.

%time X_pca = RandomizedPCA(n_components=2).fit_transform(X)
```
CPU times: user 0.02 s, sys: 0.00 s, total: 0.02 s
Wall time: 0.02 s
Out[15]:
(1797, 2)
```
- result is fast 
- img of 2D

## Overfitting
- Problem w/ training of data
- Train a Support Vector Machine naively on the digits dataset

```python
# score returned is the rate of correct classification
from sklearn.svm import SVC
SVC().fit(X, y).score(X, y)
```
Result = 1.0
 
Did we train a perfect model?     
- Impossible to tell w/o more data.

#### Next steps... 
- Split the data into a training set & a test set.
- Retrain on the train set
- Computer 

##### Overfitting
Data score is not as good as the train score
##### Underfitting
Train score is not close to 100%; accuracy is underfitted

We want neither over or under.
`test_score ~= train_score ~= 1.0`


## Cross Validation
Procedut to repeat the train/test to make more accurate estimate of real est score by ave the vals found in runs.

`sklearn.cross_validation` - utility function to compute the cross validated test scores automatically

After this, you get ... 

```
print(mean_score(test_scores))    
Mean score: 0.993 (+/-0.001)    
```

## Exercise

## Model Selection with Grid Search
- img - gammas in train & test scores
- sweet spot region for gamma around $10^4$ to $10^3$
    - gamma is too low, train score is low
    - gamma is too high
    - overfitting regime

- If c is too low, then the model will be overfitting. 
- When you over train c, the model can not overfit. 



### Which are the best values of C & gamma?    
```
from sklearn.grid_search import GridSearchCV    
...    
gs_svc.best_params_, gs_svc.best_score_    
({'C': 1.0, 'gamma': 0.001}, 0.9659957194045643)    
```

Note: helper function that is in notebook is not in scikit, however stuff like this will be added in the future. 

Q: Is the question determistic? 
A: yes. Grid search takes a long time & gives evaluations by the order you provide it.

```
display_grid_scores(gs_svc.grid_scores_, top=20)    
```

Stars in the result are there to mark overlap w/ standard error
```
C=1.0, gamma=0.001: 0.966 (+/-0.009) *      
C=10.0, gamma=0.001:    0.966 (+/-0.002) *      
C=100.0, gamma=0.001:   0.966 (+/-0.002) *      
C=10.0, gamma=0.0001:   0.966 (+/-0.008) *      
C=100.0, gamma=0.0001:  0.962 (+/-0.007) *      
C=1.0, gamma=0.0001:    0.922 (+/-0.003)      
C=0.1, gamma=0.001: 0.722 (+/-0.008)      
C=10.0, gamma=0.01: 0.314 (+/-0.018)      
... more
```

No time for the exercise. :-(

## Plotting Learning Curves for Bias-Variance analysis

### learning curves
- understand the behavior of model
- run several cross validation steps for various random sub-samples of the training set 
- plot the mean training and test errors
- imgs/01-train-set-test-scores-learning-curve.png
    - When you have few data, the model overfits
    - When you have more data, you have less overfitting, but you have slight underfitting, b/c your train score is no longer 100%
- plotting learning curves is another way to understand how the model is working

#### What does the img mean?
- if training set error is high --> high bias 
    - underfit training set.
- if testing set error is sig larger than the training set error --> 
    - model has high variance
    - overfit the training set