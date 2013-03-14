06_iris_dimensionality
# Notes: Unsupervised Learning: Dimensionality Reduction and Visualization

## Principal component analysis
- Tranform data into principal component space

## Dimentality reduction techniques 
- You take many dimensions and make them a lot less. 
- Combining multiple features

### Options
- `sklearn.decomposition.PCA`: <br/>
   Principal Component Analysis
- `sklearn.decomposition.RandomizedPCA`:<br/>
   fast non-exact PCA implementation based on a randomized algorithm
- `sklearn.decomposition.SparsePCA`:<br/>
   PCA variant including L1 penalty for sparsity
- `sklearn.decomposition.FastICA`:<br/>
   Independent Component Analysis
- `sklearn.decomposition.NMF`:<br/>
   non-negative matrix factorization
- `sklearn.manifold.LocallyLinearEmbedding`: <br/>
   nonlinear manifold learning technique based on local neighborhood geometry
- `sklearn.manifold.IsoMap`: <br/>
   nonlinear manifold learning technique based on a sparse graph algorithm