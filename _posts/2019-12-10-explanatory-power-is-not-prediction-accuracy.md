# Explanatory Power ≢ Prediction Accuracy

[2019-12-10]

![](/img/2019-12-10-a.png)

Model fit for a set of data is not an indicator of a model's predictive ability when applied to other datasets. Realisation came while looking at the barplot on the left: parsimonious variable selection models e.g. (GLMNET and LASSO) can perform worse than models without variable selection (e.g. least squares and ridge regression) for prediction.