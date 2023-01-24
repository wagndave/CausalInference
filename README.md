# CausalInference
Causal Inference Toolkit

WIP

Reference for math in Github: https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions

Reference for tables in Github: https://www.npmjs.com/package/markdown-it-multimd-table


## Assumptions

1. Stable Unit Treatment Value Assumption (SUTVA)

1.1 No intereference: units do not interefere with each other: no spillover/contagion. Treatment assignment of one unit does not affect the outcome of another unit

e.g. vaccine studies

1.2 One version of treatment

-> SUTVA allows us to write potential outcome for $i^{th}$ person in terms of only that person's treatment. This simplifies the problem.

2. Consistency

  When treatment is T=1, then Y_{1} is equal to the observed outcome if the actual treatment received is T=1. Linking potential outcomes to observed outcomes.

3. Ignorability (a.k.a 'no unmeasured confounders' 

$Y_0, Y_1 /indep A|X$
  
4. Positivity

## Instrumental variables


This is a test, and uses `$` delimiters to show math inline: $\sqrt{3x-1}+(1+x)^2$

**The Cauchy-Schwarz Inequality**

$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

testing tables:

| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff testing | git diff       | git diff      |


## Non-compliance and LATE 


## Matching 


- matching directly on confounders
- greedy matching
- optimal matching
- assessing balance


## IPTW

## Propensity Score Matching



## Difference-in-Difference (DID)




## Synthetic Control





## Regression Discontinuity Design (RDD)





