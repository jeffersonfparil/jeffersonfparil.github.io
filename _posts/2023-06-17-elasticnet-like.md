# Elasticnet-like algorithm: attempting to correct for non-orthonormality after soft-thresholding

[2023-06-17]

Let the linear model be:

$$
y = X\beta + \epsilon
$$

where $$y$$ is a vector of $n$ observations (*known*),
$X$ is the $n \times p$ matrix of explantory variables (*known*),
$\beta$ is a vector of $p$ explanatory effects (also called estimators or predictors; *unknown*), and
$\epsilon$ is the vector of residual effects (*unknown*), i.e.

$$
\epsilon \sim N(0, \sigma)
$$

hence

$$
\bar y = X\beta
$$

The objective is to estimate the explanatory effects, $\hat\beta$. 
The straightforward solution is called the ordinary least squares (OLS) solution, 
which minimises the squared differences in the predicted and observed phenotypes (cost function), i.e. 

$$
argmin_{\hat\beta} (X\hat\beta - y)^{2}
$$

OLS has a closed-form solution ($\hat\beta$ are estimated without the need for iterative optimisation minimising the above cost function), i.e. 

$$
\hat\beta = (X^{T}X)^{-1} X^{T}y
$$

Alternatively,

$$
\hat\beta = X^{T} (XX^{T})^{+}y
$$

where $A^{+}$ is the pseudoinverse of $A$.

When $n << p$, i.e. underdetermined cases,
more than 1 solution ($\hat\beta$) exists which leads to overfitting hence worse models,
i.e. not capturing the true explanatory effects. 
In these cases, the estimated effects ($\hat\beta$) need to be penalised, 
i.e. reduced to give less weights to unimportant explanatory variables. 
Ridge, least absolute shrinkage and selection operator (Lasso), and elasticnet regression are such penalised regression techniques. 
Unlike OLS, in addition to minimising the squared errors the magnitude of the explantory effects are penalised using a penalisation factor, $\lambda \in (0, +\infty)$. 
The cost function for ridge is

$$
argmin_{\hat\beta, \lambda} (X\hat\beta - y)^{2} + \lambda(\hat\beta)^{2}
$$

for Lasso it is

$$
argmin_{\hat\beta, \lambda} (X\hat\beta - y)^{2} + \lambda||\hat\beta||
$$

where $\|\|A\|\|$ is the absolute value of $A$, and elasticnet combines these two penalisations using an elastic parameter, $\alpha \in [0, 1]$ with the form

$$
argmin_{\hat\beta, \alpha, \lambda} (X\hat\beta - y)^{2} + \lambda \left ( {1-\alpha \over 2} (\hat\beta)^{2} + \alpha ||\hat\beta|| \right )
$$

These models can be solved using iterative algorithms, i.e. iteratively testing various values of $\hat\beta$, $\lambda$, and $\alpha$ which minimise the cost functions 
with the next values based on how well moving across the parameter space reduces the cost functions. This method is computationally expensive, thankfully closed-form solutions exist. 
Ridge regression has the closed-form solution,

$$
\hat\beta = (X^{T} X + \lambda I)^{-1} X^{T}y
$$

This lends to less expensive iterative solutions which will only need to find the best $\lambda$ using k-fold cross-validation, 
i.e. using a set of $\lambda$, divide the $n$ observations into $k$ groups or folds, 
(1) set aside one group for validation and using the rest of the groups to solve for $\hat\beta$ (measure the performance of the model using the validation group - cross-validation), 
(2) repeat for the rest of the folds,
(3) reshuffle, generate a new grouping, and repeat for k-fold cross-validation, 
(4) repeat the k-fold cross-validation $r$ times.

On the otherhand, closed-form solution for Lasso only exist if $X$ is orthonormal ($X^{T} = X^{-1}$ hence $\hat\beta = X^{T}y$), i.e.

$$
\hat\beta_j = 
$$




