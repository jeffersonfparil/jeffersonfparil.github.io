# Violinplotter version 3.0.0 with nonparametric mean comparison

[2021-11-17]

![](/img/2021-11-17.png)

Violinplotter version 3 is out! Now with nonparametric pairwise mean comparison via the Mann-Whitney test as default.

```
violinplotter(formula, 
              data=NULL, 
              TITLE="", 
              XLAB="", 
              YLAB="", 
              VIOLIN_COLOURS=c("#e0f3db", "#ccebc5", "#a8ddb5", "#7bccc4", "#4eb3d3", "#2b8cbe"), 
              PLOT_BARS=TRUE, 
              ERROR_BAR_COLOURS=c("#636363", "#1c9099", "#de2d26"), 
              SHOW_SAMPLE_SIZE=FALSE, 
              SHOW_MEANS=TRUE, 
              CATEGORICAL=TRUE, 
              LOGX=FALSE, 
              LOGX_BASE=10, 
              MANN_WHITNEY=TRUE, 
              HSD=FALSE, 
              ALPHA=0.05, 
              REGRESS=FALSE)
```