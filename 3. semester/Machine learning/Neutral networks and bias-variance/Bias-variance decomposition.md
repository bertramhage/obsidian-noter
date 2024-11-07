# Bias-variance

> Lecture 8 - 24/10/23

### What is bias and variance

![Skærmbillede 2023-10-24 kl. 13.17.12.png](Skærmbillede%202023-10-24%20kl.%2013.17.12.png.md)

### Regualized least squares

###### Cost function from linear regression

$$
E(\mathbf{w}) = ||\mathbf{y}-\tilde{\mathbf{X}}\mathbf{w}||^2
$$

Introduce regularization term $\lambda||\mathbf{w}||^2$ to penalize large weights:

$$
E_\lambda\left(\boldsymbol{w}, w_0\right)=\sum_{i=1}^N\left(y_i-w_0-\hat{\boldsymbol{x}}_i^{\top} \boldsymbol{w}\right)^2+\lambda\|\boldsymbol{w}\|^2=\left\|\boldsymbol{y}-w_0 \mathbf{1}-\hat{\boldsymbol{X}} \boldsymbol{w}\right\|^2+\lambda\|\boldsymbol{w}\|^2
$$

$$
w_0 = \mathbb{E}[y], \mathbf{w^*} = (\mathbf{\hat{X}}^T\mathbf{\hat{X}}+\lambda\mathbf{I})/(\mathbf{\hat{X}}^T\mathbf{\hat{y}})
$$
, where $\hat{\mathbf{X}}$ is the standardized feature matrix.
If $\lambda=0$ then no effect, else if $\lambda \rightarrow\infty, \mathbf{w^*}\rightarrow0$.

<img title="" src="file:///var/folders/sq/wx9hvn512t98113z7jvv2j7m0000gn/T/TemporaryItems/NSIRD_screencaptureui_50O6I9/Skærmbillede%202023-10-24%20kl.%2013.30.51.png" alt="Skærmbillede 2023-10-24 kl. 13.30.51.png" width="563" data-align="center">

Top graphs have high variance, low bias. Bottom graphs have low variance high bias.

<img title="" src="file:///Users/bertramhage/Desktop/Skærmbillede%202023-10-24%20kl.%2013.51.27.png" alt="Skærmbillede 2023-10-24 kl. 13.51.27.png" width="401" data-align="center">

<img title="" src="file:///var/folders/sq/wx9hvn512t98113z7jvv2j7m0000gn/T/TemporaryItems/NSIRD_screencaptureui_N1fbfU/Skærmbillede%202023-10-24%20kl.%2014.01.55.png" alt="Skærmbillede 2023-10-24 kl. 14.01.55.png" width="322" data-align="center">

### Bias-variance decomposition

$$
\begin{aligned}
\mathbb{E}_{\mathcal{D}}\left[E^{\text {gen }}\right] & =\mathbb{E}_{\boldsymbol{x}}\left[\mathbb{E}_{\mathcal{D}, y \mid \boldsymbol{x}}\left[\left(y-f_{\mathcal{D}}(\boldsymbol{x})\right)^2\right]\right] \\
\mathbb{E}_{\mathcal{D}}\left[E^{\text {gen }}\right] & =\mathbb{E}_{\boldsymbol{x}}\left[\operatorname{Var}_{y \mid \boldsymbol{x}}[y]+(\bar{y}(\boldsymbol{x})-\bar{f}(\boldsymbol{x}))^2+\operatorname{Var}_{\mathcal{D}}\left[f_{\mathcal{D}}(\boldsymbol{x})\right]\right]
\end{aligned}
$$

###### Explanation of last expression

The first term does not depend at all upon our choice of model but simply represent the intrinsic difficulty of the problem. We cannot make this term any larger or smaller by selecting one model over another.

The second term is the **bias** term. It tells us how much the average values of models trained on different training datasets differ compared to the true mean of the data.

The third term is the **variance** term. It tells us how much the model wiggles when trained on different sets of training data. That is, when you train the models on $N$ different (random) sets of training data and the models (the prediction curves) are nearly the same this term is small
