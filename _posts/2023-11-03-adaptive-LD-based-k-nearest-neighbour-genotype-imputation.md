# Adaptive linkage disequilibrium (LD)-based k-nearest neighbour imputation of genotype data

[2023-11-03]

This is an attempt to extend the [LD-kNNi method of Money et al, 2015, i.e. LinkImpute](https://doi.org/10.1534/g3.115.021667), which was an extension of the [kNN imputation of Troyanskaya et al, 2001](https://doi.org/10.1093/bioinformatics/17.6.520). Similar to LD-kNNi, LD is estimated using Pearson's product moment correlation across loci per pair of samples, but instead of computing this across all the loci, we divide the genome into windows which respect chromosomal/scaffold boundaries. We use Euclidean distance which accomodates for continuous allele frequencies instead of genotype classes as in taxicab or Manhattan distance used in LD-kNNi. The adaptive behavior of our algorithm can be described in cases where the sparsity in the data is too high resulting to:
  - completely undefined correlation (LD) matrix, at which point we will use all the loci to compute distances between samples, and when
  - all k-nearest neighbours are missing at the locus which needs to be imputed, then we increase `k` until one of the neighbours has data to be used for weighted imputation of the missing allele.
