# Happy holidays!

[2021-12-23]

![](/img/2021-12-23.png)

R Christmas tree.

```
x = rnorm(1e6, mean=0, sd=0.1)
d = density(x)
colour_leaves = rgb(165/256, 215/256, 85/256)

par(bg = 'black')

plot(d, xlim=c(-0.5,0.5), ylim=c(0,5))
mtext("Happy Holidays!", cex=3, col="white")
grid()
polygon(d, col=colour_leaves, border=colour_leaves)

colour_star_border = 
colour_star_border = "yellow"
colour_star_fill = "yellow"
points(x=0, y=4.5, pch=24, col=colour_star_border, bg=colour_star_fill, cex=5)
points(x=0, y=4.5, pch=25, col=colour_star_border, bg=colour_star_fill, cex=5)
points(x=0, y=4.5, pch=24, col=colour_star_border, bg=NA, cex=5)

n_balls = 50
idx = sample(c(1:length(d$x))[(d$x>-0.2) & (d$x<0.2) & (d$y<4)], n_balls)
x_balls = d$x[idx]
y_balls = lapply(d$y[idx], FUN=function(x){sample(seq(0.5, x, length=10),1)})
colours_balls = sample(rainbow(100), n_balls)
for (i in 1:n_balls){
    points(x_balls[i], y_balls[i], pch=19, col=colours_balls[i], cex=1)
}

colour_trunk = rgb(140/255, 80/255, 50/255)
points(x=rep(0,5), y=seq(0,1,length=5), pch=15, cex=5, col=colour_trunk)

```