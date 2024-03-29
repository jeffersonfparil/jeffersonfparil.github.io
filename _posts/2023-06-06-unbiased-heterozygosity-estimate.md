# Unbiased expected heterozygosity estimate from allele frequencies

[2023-06-06]

For a biallelic locus: 

$$ 
h = \frac{n}{n-1} \left( 2pq \right)
$$

For a multiallelic locus with $m$ alleles: 

$$
h = \frac{n}{n-1} (1 - \sum^m_i{p^2_i})
$$

It follows that unbiased homozygosity is defined as: 

$$ 
h_o = 1 - h \ 
= 1 - \frac{n}{n-1} (1 - \sum^m_i{p^2_i})
$$
