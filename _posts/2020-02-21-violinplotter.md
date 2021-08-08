# violinplotter

[2020-02-21]

![](/img/2020-02-21.png)

In my attempt at publishing an R package in CRAN I have used these R commands a hecking lot!
```
library(devtools)
create("violinplotter")
check()
document()
build()
release()
```
```
Rscript -e "devtools::document(); devtools::build()"; cd ..; R CMD check violinplotter_*; cd -
```
```
library(remotes) ### great light-weight library for installing packages from git repos
install_github("jeffersonfparil/violinplotter")
```
Anyway, check out [violinplotter package](https://github.com/jeffersonfparil/violinplotter) if you're interested in comparing means of stuff.