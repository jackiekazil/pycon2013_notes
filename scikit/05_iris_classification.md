05_iris_classification

# Notes: Supervised Learning: Classification of Iris Data

- Load the iris data
- LinearSVC (support vector classifier)
- in ipython notebook -- get help
```python
?LinearSVC
```
- X is the iris data
- y is the iris 

### Items learned
- Everything with a trailing underscore is learned while training
- Examples
    - clf.coef_
    - clf.intercept_

### Ideas for feature classifications
- Emails by feature
- Faces by features

### How to approach the exercise
- Instainiate the model
- call the fit method
- call the predict method

Recommendation for how to decide which one to do -- 
http://peekaboo-vision.blogspot.com/2013/01/machine-learning-cheat-sheet-for-scikit.html

## Probabilistic 

### Example
- print clf2.predict_proba(X_new)
- [[  9.07512928e-01   9.24770379e-02   1.00343962e-05]]
- It is highest probability of being the first one, least probability of the last.

### Evaluating the model
- print y_model == y
- We usually don't expect the data to be this good normally. We will talk about this more ... soon.
