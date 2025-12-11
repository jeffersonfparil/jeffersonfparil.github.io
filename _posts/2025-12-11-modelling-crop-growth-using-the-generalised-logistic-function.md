# Crop growth modelling using the generalised logistic function

[2025-12-11]

The generalised logisitic model for crop growth can be defined as:

$$
y(t) = {A + {{K-A} \over {C + (Qe^{-Bt})^{1/v}}}}
$$

where:

- $y(t)$: biomass at time $t$
- $A$: lower asymptote (initial or minimum biomass)
- $K$: positively affects the upper asymptote. This is the final or maximum biomass if:
    + $C = 1.00$, since:
    + $y_{max} = A + (K-A)/C^{1/v}$, then 
    + $y_{max} = A + K - A$, therefore: 
    + $y_{max} = K$
- $C$: negatively affects the final or maximum biomass
- $Q$: negatively affects initial or minimum biomass
- $e$: Euler's number (~2.71828)
- $B$: growth rate
- $v$: asymmetry parameter ($v ≥ 0$; small values: fast growth early; large values: fast growth later)

To solve for $t$ at specific $y$:

$$
t(y) = -{{1} \over {B}} \log {\left( { {{1} \over {Q}} \left( \left( {K - A} \over {y - A} \right)^v - C \right) } \right) }
$$
