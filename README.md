# Causal Inference
Causal Inference Toolkit

WIP

Reference for math in Github: https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions

Reference for tables in Github: https://www.npmjs.com/package/markdown-it-multimd-table


## Assumptions

1. Stable Unit Treatment Value Assumption (SUTVA)

  1.1 No interference: units do not interfere with each other: no spillover/contagion. Treatment assignment of one unit does not affect the outcome of another unit

e.g. vaccine studies

  1.2 One version of treatment

-> SUTVA allows us to write potential outcome for $i^{th}$ person in terms of only that person's treatment. This simplifies the problem.

2. Consistency

  When treatment is T=1, then Y_{1} is equal to the observed outcome if the actual treatment received is T=1. Linking potential outcomes to observed outcomes.

3. Ignorability (a.k.a 'no unmeasured confounders')

$Y_0, Y_1 \perp A|X$
  
4. Positivity

## Instrumental variables

TLDR

In Instrumental variable (IV) analysis, we're interested in estimating local treatment effects, i.e. local causal effects, or Complier Average Causal effects (CACE). We are focused on the subset of compliers.

Problem

Theory

- the target of inference is: 




$$E(Y_{Z=1}|T_0=0,T_1=1) - E(Y_{Z=0} | T_0=0, T_1=1)$$

$$=E(Y_{z=1}-Y_{z=0}|compliers) (1)$$

$$=E(Y_{T=1}-Y_{T=0}|compliers)(2)$$

Expression (2) is true because you are restricting to the subpopulation of compliers (i.e. compliers do what they are told). In other words, $z=1$ for compliers is also going to correspond to exactly $T=1$. So as long as you are resticting to the subpopulation of compliers, you can use $z$ and $T$ interchangeably.

This is a causal effect of treatment received
.
This is a causal effect because it contrasts counterfactuals in a common population. 

But it's in a subpopulation, so it's a local efect - i.e. it's only looking at compliers. This is also referred to as complier average causal effect (CACE).  Otherwise also called Local Average Treatment Effect (LATE), which is a more general term about causal effects of subpopulations. 

Note: You have no inference about defiers, always-takers, or never-takers.


Assumptions of IV

1. exclusion restriction
2. monotonicity

i.e there is no people that do the opposite of what they are encouraged to do[^1]

Implementation

Python

```Python
from linearmodels.iv import IV2SLS

def parse(model, exog="years_of_schooling"):
    param = model.params[exog]
    se = model.std_errors[exog]
    p_val = model.pvalues[exog]
    print(f"Parameter: {param}")
    print(f"SE: {se}")
    print(f"95 CI: {(-1.96*se,1.96*se) + param}")
    print(f"P-value: {p_val}")
    
formula = 'log_wage ~ 1 + C(year_of_birth) + C(state_of_birth) + [years_of_schooling ~ q4]'
iv2sls = IV2SLS.from_formula(formula, factor_data).fit()
parse(iv2sls)


```


R

```R


````

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




## Propensity Score Matching


## Doubly-robust estimator


## IPTW

- TLDR
- problem
- theory
  - marginal structural models (MSM)
  
Bias-variance trade-off
There is a bias-variance tradeoff at work in propensity score estimation; every step toward better balance usually means an increase in variance and at some point a marginal decrease in bias may not be worth the associated increase in variance.

- implementation
- Papers

Python


R



- issues


## Difference-in-Difference (DID)




## Synthetic Control





## Regression Discontinuity Design (RDD)




# Special topics

## Uplift modeling

https://pylift.readthedocs.io/en/latest/introduction.html

https://github.com/rsyi/pylift/blob/master/docs/introduction.rst

https://matheusfacure.github.io/python-causality-handbook/19-Evaluating-Causal-Models.html

https://proceedings.mlr.press/v67/gutierrez17a/gutierrez17a.pdf




## Sources 

https://matheusfacure.github.io/python-causality-handbook/08-Instrumental-Variables.html

Angrist, J. D., and Jorn-Steffen Pischke. 2008. Mostly Harmless Econometrics. Princeton, NJ: Princeton University Press.

[^1]: testing footnote here.


