# Machine epsilon ($\epsilon$)

[2023-06-09]

Nulls or NA's or NAN from $0.0 \over 0.0$ can be prevented with the addition of machine epsilon to the denominator, i.e. $0.0 \over 0.0 + \epsilon$ which will yield the expected $0.0$.
Machine epsilon ($\epsilon$) is the smallest number a computer recongnises as greater than zero. It can also be interpretted as the rounding error in floating point (numbers with decimal points) arithmetic.
