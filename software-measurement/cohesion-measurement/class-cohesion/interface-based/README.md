# Interface-Based Cohesion Metrics

## Usage

Evaluate cohesion among methods of a class early in the analysis and design phase.

## Metrics

- Cohesion Among Methods of Classes (CAMC)

- Union of all parameters of all methods of a class, `U` (The Universal set)
- `Mi` is the set of parameters of a particular method `i`
- `Pi` is the intersection of `Mi` and `U`
- `ri` is the ratio `A(Pi)/A(U)`
- `sum(ri, i from 1 to k)/k*A(U)`