---
Uge: Uge 11 - 14/11/23
Pensum: Kap. 18
---
### Normal distribution
Probability density function describes the relative chance of a given value to occur
$$
p(x)=\frac{1}{\sqrt{ 2\pi \sigma^2 }}\exp\left( -\frac{(x-\mu)^2}{2 \sigma^2} \right)
$$
![[Skærmbillede 2023-11-14 kl. 14.17.33.png]]

Normal distribution characterized by mean and variance

#### Multivariate Normal distribution
$$
N(x|\mu,\Sigma) = \frac{1}{\sqrt{ (2\pi)^d |\Sigma| }}e^{-1/2(x-\mu)^T\Sigma^{-1}(x-\mu)}
$$
![[Skærmbillede 2023-11-14 kl. 14.20.17.png]]
##### 2-dimensions
$$
\mu=\begin{bmatrix}
\bar{x}_{1}\\\bar{x}_{2}
\end{bmatrix}
$$
$$
\Sigma = \begin{bmatrix}
var(x_{1}) & cov(x_{1},x_{2}) \\
cov(x_{1},x_{2}) & var(x_{2})
\end{bmatrix}
$$
###### Example
![[Skærmbillede 2023-11-14 kl. 14.22.10.png]]
### EM algorithm
Select an initial set of model parameters (mean and covariance for each cluster)

**Repeat**
- **Expectation**
	- For each object, calculate the probability of belonging to each distribution
- **Maximization**
	- For each probability distribution, estimate parameters by maximum likelihood
**Until** the parameters do not change

##### E-step
$$
p(Z_{n}=k|x_{n})=\frac{w_{k}N(x|\mu_{(k)}, \Sigma_{(k)})}{\sum_{K=1}^K w_{k}N(x|\mu_{(k)}, \Sigma_{(k)})}
$$
##### M-step
$$
N_{k} = \sum_{n=1}^N p(z_{n}=k|x_{n})
$$
$$
\mu_{(k)}=\frac{1}{N_{k}}\sum_{n=1}^N p(z_{n}=k|x_{n})
$$
$$
w_{k} = \frac{N_{k}}{N}
$$
$$
\Sigma_{(k)}= \frac{1}{N_{k}}\sum_{n=1}^N (x_{n}-\mu_{(k)})(x_{n}-\mu_{(k)})^Tp(z_{n}=k|x_{n})
$$
### Complexity controll
Selecting complexity using crossvalidation

EM initial solution:
![[Skærmbillede 2023-11-14 kl. 14.29.20.png]]
EM 5th iteration:
![[Skærmbillede 2023-11-14 kl. 14.30.01.png]]

## Anomaly detection

#### Definition
- Given a collection of data objects
	- Each object has associated a number of features
- Detect which objects deviate from normal behavior

###### Examples
- Credit card fraud detection
- Network intrusion detection
- Ecosystem disturbances
- Health and medicine monitoring
- Fault detection in industry systems
- Detection of outliers in data measurement

### Inverse distance density estimation
##### Distance based measure of density
- Density is inverse proportional to average distance to k nearest neighbors
- Density is low if nearest neightbors are far away
$$
\text{density}_{X_{\i}}(x_{i},K)=\frac{1}{\frac{1}{K}\sum_{x'\in N_{X_{i}}(x_{\i},K)} d(x_{i},x')}
$$
##### Relative density
- Density compared to density at nearest neighbors
$$
\text{density}_{X_{\i}}(x_{i},K)=\frac{\text{density}_{X_{\j}}(x_{j},K)}{\frac{1}{K}\sum_{x'\in N_{X_{i}}(x_{\i},K)} \text{density}_{X_{\j}}(x_{j},K)}
$$
## Kernel density
>[!info] Kernel density given width $\lambda$
>The formula for kernel density estimation is given
>$$
>p(\mathbf{x})=\frac{1}{N}\sum_{i=1}^{N}\mathcal{N}(\mathbf{x}|\mathbf{x}_i, \lambda^2\mathbf{I})  \, 
>$$
>and
>$$
>\mathcal{N}(\mathbf{x}|\mathbf{x}_i, \lambda^2\mathbf{I})=\frac{1}{\sqrt{ (2\pi\lambda^2)^k }}\exp\left( \frac{-\mid\mid \mathbf{x}-\mathbf{x}_i\mid\mid_2^2}{2\lambda^2} \right).
>$$

