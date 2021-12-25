# Fisher's allele diffusion equations

[2021-04-28]

![](/img/2021-04-28-a.png)

Let $p$ be the frequency of the allele of interest on a biallelic locus, $q$ is the frequency of the alternative allele, m is the selection intensity for the allele of interest, $x$ is the coordinate in a linear habitat (we're considering a one-dimensional habitat for simplicity), $t$ is the time in generations, and $k$ is the diffusion coefficient which is a function of migration or gene flow.

This is analogous to the [heat equation](https://en.wikipedia.org/wiki/Heat_equation), but with the term $mpq$ added to modulate the rates at which the areas of high curvature flattens towards the equilibrium.

An illustration of the diffusion of an allele across a linear landscape:

![](/img/2021-04-28-b.png)

Rscript used to generate the illustration above:

```{R}
N_pdf = function(x, mu=0, sigma=1){
    (1 / (sigma*sqrt(2*pi))) * exp(-(1/2)*( ((x-mu)/sigma)^2 ))
}
mu = 5
x = seq(0, 10, length=100)
y = N_pdf(x=x, mu=mu, sigma=1)
plot(x, y, type="n", xlab="x-coordinate", ylab="allele frequency (p)")
grid()
y_max = 0.3
sigmas = c(1.0, 1.1, 1.2, 1.5, 2.0, 3.0, 10)
colours = c("#4575b4", "#91bfdb", "#addd8e", "#41ab5d", "#fee090", "#fc8d59", "#d73027")
for (i in 1:length(sigmas)){
    y = N_pdf(x=x, mu=mu, sigma=sigmas[i])
    if (max(y) < y_max){
        y = y + (y_max - max(y))
    }
    lines(x=x, y=y, col=colours[i], lwd=2)
}
legend("topright", legend=paste0("t=", 1:length(sigmas)), fill=colours, bg="white")
arrows(x0=mu, y0=0.4, x1=mu, y1=y_max, lwd=2, col="gray")
arrows(x0=1, y0=0, x1=1, y1=y_max, lwd=2, col="gray")
arrows(x0=9, y0=0, x1=9, y1=y_max, lwd=2, col="gray")

```

Reference:
[FISHER, R.A. (1937), THE WAVE OF ADVANCE OF ADVANTAGEOUS GENES. Annals of Eugenics, 7: 355-369. https://doi.org/10.1111/j.1469-1809.1937.tb02153.x](https://onlinelibrary.wiley.com/action/showCitFormats?doi=10.1111%2Fj.1469-1809.1937.tb02153.x)
