# Be careful with the precision of numbers in R

[2021-01-07]

In reality, 10,000,000 / 3 = 3,333,333.333...
However, computing this in R will round this to 3,333,333. No decimal places.
Likewise, instead of showing that 10,000,001 / 5 = 2,000,000.20, R rounds the answer to the integer 2,000,000.

In Python, this rounding off is suppressed by implying that either or both the divisor and dividend are floating point numbers, e.g. 10000001.0/5

In Julia, the quotient is expressed in scientific notation, and so this is avoided.

However, it is important to note here that limits in precision exist regardless of the language used. But my point here is that, the limit in R is 1x10^7.