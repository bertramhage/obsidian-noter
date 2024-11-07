# Clustering

> Uge 10 – 7/10/23
> 
> Chap. 18

![[Skærmbillede 2023-12-02 kl. 13.36.31.png]]

- No output variables

- Trying to learn structure, regularities, hidden information, etc.
### Clustering

- Divide data into groups (subsets/clusters) that are mearningful and useful.

- Observations in the same cluster are similar in some sense.

##### Partitional / hierarchical clustering
![[Skærmbillede 2023-12-02 kl. 13.39.21.png]]
#### Types of clusters

###### Well seperated
![[Skærmbillede 2023-12-02 kl. 13.39.38.png]]

###### Center based
![[Skærmbillede 2023-12-02 kl. 13.39.56.png]]
###### Contiguity-based

Each point is closer to at least one point in its cluster than to any point in another cluster
![[Skærmbillede 2023-12-02 kl. 13.40.11.png]]
###### Density-based
![[Skærmbillede 2023-12-02 kl. 13.40.35.png]]
### K-means clustering

Select K points as initial centroids
**Repeat**
Form K clusters by assigning each point to its closest centroid
Recompute the centroids of each cluster
**Until** centroids do not change
![[samlet-2-12-23.png]]
##### How do I...

- Find the closest centroid?:
  
  - Use a suitable dissimilarity/similarity measure

- Compute the cluster centroids?:
  
  - Depends on dissimilarity/similarity measure
  
  - For example, for euclidian distance the mean is optimal

### Agglomerative hierarchical clustering

Compute the proximity matrix
**Repeat**
Merge the two closest clusters
Update the proximity matrix to reflect the proximity between the new cluster and the original clusters
**Until** only one cluster remains

##### Dendogram
![[Skærmbillede 2023-12-02 kl. 14.30.19.png]]
#### Proximity between clusters

###### Minimum (single linkage)

$$
proximity(C_i, C_j) = min_{x \in C_i, y\in C_j} d(x,y)
$$

###### Maximum (complete linkage)

$$
proximity(C_i, C_j) = max_{x \in C_i, y \in C_j} d(x,y)
$$

###### Group average

$$
proximity(C_i, C_j) = \frac{\sum_{x\in C_i, y\in C_j} d(x,y)}{m_im_j}
$$

where

- $C_i$: Observations in cluster $i$

- $C_j$: Observations in cluster $j$

- $m_i$: Number of observations in cluster $i$

- $m_j$: Number of observations in cluster $j$



##### Ward's method

Increase in sum of squared error after merging the two clusters should be as small as possible.



#### Comparing partitions - Jarccard and SMC/Rand index

###### Rand index (SMC)

$$
R(Z,Q) = \frac{S+D}{1/2N(N-1)}
$$

###### Jaccard similarity

$$
J(Z,Q) = \frac{S}{1/2N(N-1)-D}
$$

where

- $S = \{\text{Number of pairs in the same cluster in Z and Q}\}$ 

- $D = \{\text{Number of pairs in different clusters in Z and Q}\}$

##### A general approach - an efficient encoding

$$
n_{km} = \{ \text{Observations assigned to cluster k in Z and m in Q}\}=
\sum_{i=1}^N \sum_{j=1}^N \delta_{z_i, k}\delta_{z_j,m}
$$

$$
n^Z = \{ \text{Number of observations in k in Z}\} = 
\sum_{k=1}^K n_{km}
$$

$$
n^Q = \{ \text{Number of observations in m in Q}\} = 
\sum_{m=1}^M n_{km}
$$

Any two observations $i$, $j$ can either be in the same cluster, or in different clusters.

There are $1/2 N(N-1)$ pairs in total.

We get to $1/2N(N-1)$-long binary vectors corresponding to each pair $i, j$

$$
S= \{ \text{Number of pairs i, j in the same cluster in Z,Q}\}\\
$$
$$
D = \{ \text{Number of pairs i, j in different clusters in Z,Q}\}
$$
$$
S=\sum_{k=1}^{K}\sum_{m=1}^{M} \frac{n_{km}(n_{km}-1)}{2} \,   \, 
$$
$$
D = \frac{N(N-1)}{2}-\sum_{k=1}^{K} \frac{n_k^Z(n_k^Z-1)}{2}  \, -\sum_{m=1}^{M} \frac{n_m^Q(n_m^Q-1)}{2}  \,+S 
$$
###### Example
![[Skærmbillede 2023-12-02 kl. 14.34.13.png]]
$$
Z = [1, 1, 2, 2, 2, 3, 3, 3, 3,3]\\
Q = [1,1,3,1,1,1,1,3,3,2]
$$

$$
$$

$$n=
\overbrace{ \begin{bmatrix}2 & 0 & 0 \\ 2 & 0 & 1\\ 2 & 1 & 2\end{bmatrix} }^{ Q }
\begin{rcases}
\\ \\ \\
\end{rcases}
Z
$$

$$
n^Z = \begin{bmatrix}2 & 3 & 5 \end{bmatrix}\\
n^Q = \begin{bmatrix}6 & 1 & 3 \end{bmatrix}
$$

$$
S = \sum_{km} \frac{1}{2}n_{km}(n_{km}-1)=4 \frac{1}{2}(2(2-1))=4
$$
$$
\begin{align} \\
D&=\frac{1}{2}10(10-1)-\sum_k \frac{1}{2}n^2_k(n^2_k-1)-\sum_m \frac{1}{2}n^Q(n^Q-1)+S\\
&=45-\left( \frac{2(2-1)}{2}+\frac{3(3-1)}{2}+\frac{5(5-1)}{2} \right)-\left( \frac{6(6-1)}{2}+0+\frac{3(3-1)}{2} \right)\\&=45-14-18+4=17
\end{align}
$$

#### Entropy and mutual information recap

Consider a probability distribution $P(X = x_i) = p_i, i=1,2,..., n$

Information obtained from observing $x_i$ is 

$$
I = -\log(p_i)
$$

Average information obtained is called entropy

$$
H[p_X] = \mathbb{E}[I] = -\sum_{i=1}^np_i\log p_i
$$

Entropy is defined for general densities $P(X = x_i, Y=y_j)=p_{ij}$

$$
H[p_{XY}] = -\sum_{i=1}^n\sum_{j=1}^m p_{ij}\log p_{ij}
$$

The **Mutual information** is defined as

$$
MI[X, Y] = H[P_X] + H[P_Y]-H[P_{XY}]
$$


