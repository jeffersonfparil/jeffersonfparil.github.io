# Approximate Bayesian computation (ABC) for genomic prediction and association (GPAS) resource optimization (part 1)

[2019-11-18]

![](/img/2019-11-18-b.png)

As a component of my chapter in Quantitative Genetics, I'm trying to use ABC to optimize resource allocation for GPAS (genome-wide association and genomic prediction experiments). For this I'm currently playing around with the abc package in R.

Approximate Bayesian Computation (ABC) tries to find the best parameters and/or model that fit observed data through repeated simulations with some acceptance-rejection method.

I need to simulate the the data (`y|params`; where `y={correlation, log10(RMSD+1), TPR and FPR}`) and so I need to define the parameter space as `params ~ Unif(min=0, max=1)` where `sum(params) = 1`.
