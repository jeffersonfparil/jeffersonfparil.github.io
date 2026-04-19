# Multi-layer Perceptrons for Yield Trial Analysis

[2026-04-19]

![](/img/2026-04-19.png)

I have a feeling that MLP (multi-layer perceptrons --> the generic version of artificial neural networks for deep learning) 
can be useful in analysing yield trials, especially complex and unbalanced multi-year, multi-environmnent, multi-management,
multi-treatment crop yield trials (even ecological studies with unbalanced designs).

What I imagine is that using an MLP with an automatic hyperparameter optimisation step or simply just using a few hidden layers with not too many hidden nodes,
together with a lot of training epochs with some early stopping threshold is much simpler than the artistic pursuit for the best model during model selection 
in linear mixed modelling.

Here's the tool I'm building from scratch which will attempt to achieve this: [https://github.com/jeffersonfparil/mlp](https://github.com/jeffersonfparil/mlp).
