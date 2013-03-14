09_validation_and_testing

# Notes: Measuring Classification Performance: Validation & Testing

```python
# Instantiate and train the classifier
from sklearn.svm import LinearSVC
clf = LinearSVC(loss = 'l2')
clf.fit(X, y)
```

```python
# Check input vs. output labels
y_pred = clf.predict(X)
print (y_pred == y)
```

#### Problem!
- We are checking the performance of the estimator based on values that it was trained on


### A Better Approach: Cross-Validation
- Now we train on the training data, and test on the testing data:    
[ True  True  True  True  True  True  True  True  True  True  True  True
  True  True  True  True  True  True  True  True  True False  True  True
  True  True  True  True  True  True  True False  True  True  True  True
  True False]


## Diving Deeper: Hyperparameters, Over-fitting, and Under-fitting
- In the real world - how to actually spend your money further 
- Recommendation - Andrew Ng's excellent
Coursera course, available here:* https://www.coursera.org/course/ml

### What to do? How to decide
- Use simpler or more complicated model?
- Add more features to each observed data point?
- Add more training samples?

We are going to look as small sets of data, but it scales up.

### Simple regression problem
- Hyper param we choose is the degree 
- If we change it to 1, then we get a line

If we add noise to the data, then it becomes more interesting. 
### Adding noise 
- If u add noise, then it get m
- If you mess w/ the degree, then the RMS error lessons
- If you raise your degree, then the RMS error lessons
- If you 
 - This shows us the bias variance trade off. 

## bias & variance

Bias model - no matter how well you adjust the params, the line will never fit.

High variance model - model changes greatly when you move a point.

Issue you have --    
- you try to trade off between bias & variance
- bias - you have consistancy, but the line doesn't often fit everything.
- variance - you have inconsistancy, but it fits more
- be able to identify each 

## Validation Curves
- image in imgs
- when looking at validation...
    - we want the point in the lines where the rms error (validation) is the least.

## Learning Curves
- plot of the training and cross-validation error as a function of the number of training points
- img of diagram in imgs
- validation error is always going to be curve always decreasing
- training error is going to always increase
- why?
- validation -- the more points you add, the better it gets.
- training -- the more points you add, the worse it gets, because it is more eractic. 


## Last caution
- Train the model - usually ~60% of the data
- Validation set - usually ~20% of the data
- Test set - expect error of validated model -- usually ~20% of the data


