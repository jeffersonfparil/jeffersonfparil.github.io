# Recursive allele frequency equations of W-shredder and X-shredder suppression gene drives

[2021-08-08]

## W-shredder

Applicable to ZW/ZZ sex determination systems, e.g. birds, reptiles, and lepidopteran pests, where ZW are females and ZZ are males.

$$
\begin{aligned}
Z^dW ~~— c \rightarrow~~ Z^d0
\end{aligned}
$$

The recursive drive allele frequency is:

$$
\begin{aligned}
q_{t+1} &= {8q_{t} - 3cq_{t} - cq_{t}^2 \over 8-4c},
\end{aligned}
$$

where $$q_{t}$$ is the frequency of the suppression gene drive allele at generation $$t$$, and $$c$$ is the conversion efficiency, i.e. the rate at with the W chromosome is shredded given $$Z^{d}W$$ genotypes.

## X-shredder

Applicable to XX/XY sex determination systems, e.g. mammals, where XX are females and XY are males.

$$
\begin{aligned}
XY^d ~~— c \rightarrow~~ 0Y^d
\end{aligned}
$$

The recursive drive allele frequency is:

$$
\begin{aligned}
q_{t+1} &= {2q_{t} \over 2 - c + cq_{t}},
\end{aligned}
$$

where $$q_{t}$$ is the frequency of the suppression gene drive allele at generation $$t$$, and $$c$$ is the conversion efficiency, i.e. the rate at with the X chromosome is shredded given $$XY^{d}$$ genotypes.