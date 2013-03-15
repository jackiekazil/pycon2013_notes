03 - Text Feature Extraction for Classification and Clustering

# Text Feature Extraction for Classification and Clustering

Recommends made on libraries to check out which extract features     
- http://scikit-image.org/
- http://scikit-image.org/docs/dev/auto_examples/plot_hog.html

## canonical text classification example:

- The 20 newsgroups dataset: around 18000 text posts from 20 newsgroups forums
- Bag of Words features extraction with TF-IDF weighting
- Naive Bayes classifier or Linear Support Vector Machine for the classifier itself

workflow diagram of what previously happened: 03-supervised_scikit_learn.png

#### loading the dataset

#### Extracting Text Features
- call the fit transformator 
```
%time X_train_small = vectorizer.fit_transform(twenty_train_small.data)     
CPU times: user 2.11 s, sys: 0.09 s, total: 2.20 s     
Wall time: 2.18 s     
```
```
X_train_small     
<2034x34118 sparse matrix of type '<type 'numpy.float64'>'     
    with 323433 stored elements in Compressed Sparse Row format>     
```

When you have a dataset like this, it is good to do a scatter plot of the data. Data is shared vocab.
- img: 03-text-scatterplot-of-shared-vocab.png

### Training a Classifier on Text Features
- score on the test set 
- model is both overfitting and underfitting a bit at the same time
```
clf.score(X_train_small, y_train_small)
0.99262536873156337
```

### Introspecting the Behavior of the Text Vectorizer
text vectorizer; see doc string for all the details 
```
TfidfVectorizer()
```

Convert a string into a list of word:
```
analyzer = TfidfVectorizer().build_analyzer()
analyzer("I love scikit-learn: this is a cool Python lib!")
```
out: [u'love', u'scikit', u'learn', u'this', u'is', u'cool', u'python', u'lib']

... and we ran out of time. :-(      
lucky us, the repo & notebooks are pretty complete!

- Last notebook - how to scale to larger programs
- distributed learning
- uses hassing(sp?)
