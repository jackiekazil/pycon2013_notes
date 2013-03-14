Notes from this tutorial:
# An Introduction to scikit-learn: Machine Learning in Python
Speaker: Jake Vanderplas   
https://us.pycon.org/2013/schedule/presentation/22/   
https://github.com/jakevdp/sklearn_pycon2013   

It should be noted that the notes in this tutorial area really good, so these notes weren't really fleshed out.

## Introduction notebook

Classification problem & example:
```python
# Import the example plot from the figures directory
from figures import plot_sgd_separator
plot_sgd_separator()
```
 
Regression: 
- We know the x & y, given x, we know what y is.
- Predict where on the line this data lines.

### Numpy 
- Generating arrays
- Access elements by notation 
- Transpose an array

For more info on numpy & other scipy libraries: 
http://scipy-lectures.github.com/

### Scipy Sparse Matrixes
- Not being used in this tutorial
- LIL (list in lists) matrixes
 - Issue - slower than CSC, but flexible 
- Know about these when you apply them to larger datasets

### Matplotlib
Some samples to note

```python
# imshow - note that origin is at the top-left!
plt.imshow(im)
```
```python
# imshow - note that origin is at the top-left!
plt.imshow(im)
```

## Representation and Visualization of Data (02_sklearn_data)
- Data in scikit-learn is in 2 array. 
    - Sample data - # of samples by # of features

#### Iris
- n samples by n features 
    - n samples is the # of Iris
    - n features is the color, the length of pedals, pixels on the image

- Target to target names
- Data is 4-D, but often we only look at 2 at a time
    - 4-D is the # of features -- so 4 features.
- So we set x-index & y-index
    -  Which features result in an interesting visualizations
- We are doing feature selection
    - Right now we are doing it manually, but there are tools to help you to automatically. 

### Available data 
- U can fetch from scikit
 - datasets.fetch_
- U can load a dataset that is already saved
 - datasets.load_
- Datasets are loaded into your home directory

### Loading Digits Data
n_samples, n_features = digits.data.shape   
print (n_samples, n_features)   

(1797, 64)    
- 1797 samples
- 64 features, so 64-D

- digits.data.shape == digits.images.shape
- Uses same memory:
    - (4351602688, False)   
    - (4351602688, False)   

#### Machine learning 
- You need to get your data into a format from the real world that the technology can understand. This is the hardest part.
- How example: You pick out the faces from a crowd
    - Create a classifier to identify faces via boxes
    - This is a face
    - This is a pant leg
- Features in most machine learning alogrithms has be the same length
