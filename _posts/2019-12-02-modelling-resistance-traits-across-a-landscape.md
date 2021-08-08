# Modelling resistance traits across a landscape using different interpolation methods

[2019-12-02]

![](/img/2019-12-02.png)

Simple linear interpolation via interp ([akima package](https://cran.r-project.org/web/packages/akima/index.html)) was performed and produced the plot on the left with yellow (low resistance) to red (high resistance) heatmap.

Smooth interpolation via generalized additive modelling: gam ([gmcv package](https://cran.r-project.org/web/packages/mgcv/mgcv.pdf)) was also performed and produced the graph on the bottom right. However do the spline- and tensor-based GAM interpolation need to account for physical boundaries to get more sensible resistance gradient plots? And can we acquire more data points to improve the gradient map?