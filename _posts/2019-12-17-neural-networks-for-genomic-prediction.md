# Neural networks for genomic prediction

[2019-12-17]

![](/img/2019-12-17.png)

I have constructed a neural network with 5 layers in total, one input, one output, and 3 hidden layers with sigmoid function connecting the input and the 3 hidden layers, and the number of nodes decreasing by a factor of 3 across the layers and outputting a single value for a single phenotype, Each connection between two layers is defined by: 
```
node_values_{i} = sigmoid(Weights_{i} * node_values_{i-1} + biases_{i}).
```
The cost function defined as the mean square error minimized by gradient descent with learning rate of 10%.