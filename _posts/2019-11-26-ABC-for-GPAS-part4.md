# ABC for GPAS resource optimization (part 4)

[2019-11-26]

![](/img/2019-11-26.png)

Problem statement:

- How much resources do we allocate for within or across populations and individual or pool genotyping to optimize prediction accuracy in genomic prediction and QTL detection power in genome-wide association experiments?

Constraints, variables and constants:

- Constrained by a fixed number of sequencing experiments
- 100 equidistant populations in a square lattice
- 1,000 individuals per population carrying capacity
- 10,000 loci
- 5, 10 or 100 QTL under directional selection defined by a symmetric [generalized logistic function](https://academic.oup.com/jxb/article-abstract/10/2/290/528209?redirectedFrom=fulltext) with a maximal slope of 0.25 at the median.
- 0 or 100 background selection loci under directional selection also defined by a symmetric logistic function with maximal slope of -0.25, 0.00, or 0.25.
- uniform, uni-directional or bi-directional gradients of resistance allele

The challenge is to account for landscape heterogeneity - affected by population genetic forces and highly dynamic. 