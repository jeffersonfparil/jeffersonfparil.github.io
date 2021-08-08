# Arimedhargeomean

[2021-03-12]

![](https://imgs.xkcd.com/comics/geothmetic_meandian.png)

Inspired by [Randall Munroe's post](https://xkcd.com/2435/), I made a recursive R function which calculates the arithmetic mean, median, harmonic mean, and geometric mean until they converge. The geometric mean is dropped if the product of the input is negative. :-P
```
F = function(x, epsilon=0.0001) {
    if (sd(x) < epsilon) {
            out = x[1]
    } else {
        mu_1 = mean(x)
        mu_2 = median(x)
        mu_3 = length(x) / (sum(1/x))
        prod = 1
        for (i in x) {
            prod = prod * i
        }
        mu_4 = (prod)^(1/length(x))
        if (is.na(mu_4)==TRUE){
            out = F(x=c(mu_1, mu_2, mu_3))
        } else {
            out = F(x=c(mu_1, mu_2, mu_3, mu_4))
        }
    }
    return(out)
}
```

Test:
```
x1 = 1:10
x2 = rnorm(100)
F(x=x1)
F(x=x2)
```