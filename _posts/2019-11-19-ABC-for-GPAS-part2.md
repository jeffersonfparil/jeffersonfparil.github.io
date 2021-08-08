# ABC for GPAS resource optimization (part 2)

[2019-11-19]

![](/img/2019-11-19.png)

But dang! The resulting parameter space defined in by matrix with 4 columns (1 for each parameter) and 796,902 rows (seq(from=0, to=1, by=0.01) is too big, my sampling function and R are too slow to iterate across these times 100 replications! So now I'll try to do this in Julia with parallel computation.

I've implemented Julia's [Distributed](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Core-or-Distributed-Processing-1) standard library instead of [GNU parallel](https://www.gnu.org/software/parallel/parallel_tutorial.html), and it's not as painful as when I first tried it a few months ago. The trick is to use the macro `@everywhere` to define variables and functions on all threads and that the number of parallel threads are defined via `julia -p${nCores}` or within the script via Distributed.addprocs(nCores); while defining the bash variable `export JULIA_NUM_THREADS=${nCores}` does not work for some reason I'm too lazy to find out.

The repo I'm pushing into: [genomic_prediction.git](https://gitlab.com/jeffersonfparil/genomic_prediction) with a [production-ready repo for Pool-GWAS](https://github.com/jeffersonfparil/GWAlpha.jl/tree/master).

SIDE NOTES:

- Excluding missing and NaN data types from calculations in Julia1.0.1 are frustratingly inelegant!
- `dropmissing(df)`, `skipmissing(array)`, `ismissing(array)`, and `.!isnan.(array)` are just too many different functions for something as common as missing values in data analysis.