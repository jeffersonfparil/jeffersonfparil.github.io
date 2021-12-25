# ABC for GPAS resource optimization   (part 3)

[2019-11-20]

![](/img/2019-11-20.png)

Julia with parallelization using [Distributed](https://docs.julialang.org/en/v1/stdlib/Distributed/index.html) and [SharedArrays](https://docs.julialang.org/en/v1/stdlib/SharedArrays/) packages works very well! I did not measure how long it took to finish for 1000 replications but a small-scale 100-replication simulation took approximately 1 hour on 12 threads.

The resulting csv file of parameters and corresponding summary statistics is 12GB with 176,779,000 lines excluding the header. It is too big for R to load as a dataframe on a 42GB-RAM machine. However an alternative ABC simulation file with only 100 replications is only 1.2GB with 17,677,900 lines excluding the header.

Using this 100 replication dataset and the abc package in R generated posterior distributions for the four parameters (fraction of GPAS experiments or sequencing libraries devoted for across/within and pool/individual population/population groups) given the target summary statistics of correlation=1.0, log10(RMSD+1)=0.0, true positive rate=1.0, false positive rate=0.0.

## Preliminary results\*:

For expected genomic prediction accuracies of:

- 86% correlation between observed and predicted quantitative traits, and
- 1.12\*\* units of quantitative trait value deviations; as well as

for expected QTL detection power defined by:

- 54% true positive rate, and
- 51% false positive rate;

we need to allocate GPAS efforts as (refer to figures on the left):

- 40% to individual-level data from different populations (ACROSS-INDI)
- 30% to pool-level data from different populations (ACROSS-POOL)
- 26% to pool-level data within populations (WITHIN-POOL)
- 4% to individual-level within populations (WITHIN-INDI)

Question regarding the validity and usefulness of the analysis: Do the 4 summary statistics (corr, log10(RMSD), TPR and FPR) need to have different weights during the acceptance-rejection process i.e when the main objective is genomic prediction instead of QTL detection and vice versa?


Notes: 
- \*Random sampling across populations data need to be excluded and only account for the square-area grouping sampling strategy (exclusion can only happen before merging all the cross-validation outputs). Also the central tendencies (means) across these posterior distributions may need to be recalculated using maximum likelihood.
- \*\*RMSD = 1.12 = 10^(0.05)