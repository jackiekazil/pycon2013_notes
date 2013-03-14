04_houses_regression

# Supervised Learning: Regression of Housing Data

- Given the attributes of neighborhoods can we predict home price. 
- First we should visual our data in general 

### Exercises:

# Prices on feature 5 coorlate well -- feature 5 is # of rooms in the house
plt.scatter(data.data[:, 5], data.target)

# This is a categorical feature - so this wouldn't be as helpful at finding the price
plt.scatter(data.data[:, 3], data.target)

#### Decision tree vs Linear regression
- Validation against validation 
- We train the model on part of the data, then evaluate the model on the rest of the data.
- Decision tree regression 
    - The importance of this is to make sure that your model is actually doing what is should be doing.

 
