# "FALSE POSITIVE RATE" misdefined

[2019-12-05]

[and updated on 2019-12-13]

![](/img/2019-12-05.png)

I've misdefined "FALSE POSITIVE RATE" in my [GPAS resource allocation optimisation scripts](https://gitlab.com/jeffersonfparil/genomic_prediction). I'm also coining the word "misdefined" to mean incorrectly attributing a word with a concept but the concept is still kind of novel and useful*. 

In statistics False Positive Rate also known as Type I error rate defined as the probability of rejecting the null hypothesis given that the null hypothesis is true. However, in my GPAS resource allocation optimisation I used "False Positive Rate" to mean the probability of the null hypothesis given that the null hypothesis is rejected. In GWAS terms, I calculated it as the number of non-causal loci above the significance threshold divided by the total number of loci above the significance threshold. (Refer to the table on the left)

Whether this concept of:
```
P(null | reject null) = non-causal loci above threshold / total loci above threshold
```
is useful remain to be seen.

Looking through a Bayesian lens:
```
P(null | reject null)
= P(reject null | null) * P(null) / P(reject null)
= (false positive rate) * ((nLoci-nCausal)/nLoci) / (nLoci above significance threshold)
```
We can see that our weird GWAS metric P(null | reject null) is positively proportional to the real false positive rate, but will increase with decreasing number of causal loci.
*Note: This sentence is a joke. I am not really coining this non-existent word.

[UPDATE!]

It is called [False Discovery Rate (FDR)](https://en.wikipedia.org/wiki/Positive_and_negative_predictive_values)!
