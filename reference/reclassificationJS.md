# reclassificationJS: Function for reclassification table and statistics

Modified function of PredictABEL::reclassification: return output table

## Usage

``` r
reclassificationJS(
  data,
  cOutcome,
  predrisk1,
  predrisk2,
  cutoff,
  dec.value = 3,
  dec.p = 3
)
```

## Arguments

- data:

  Data frame or matrix that includes the outcome and predictors
  variables.

- cOutcome:

  Column number of the outcome variable.

- predrisk1:

  Vector of predicted risks of all individuals using initial model.

- predrisk2:

  Vector of predicted risks of all individuals using updated model.

- cutoff:

  Cutoff values for risk categories. Define the cut-off values. Ex:
  c(0,.20,.30,1)

- dec.value:

  digits of value, Default: 4

- dec.p:

  digits of p, Default: 3

## Value

Table including NRI(categorical), NRI(continuous), IDI with 95

## Details

Modified function of PredictABEL::reclassification

## See also

[`rcorrp.cens`](https://rdrr.io/pkg/Hmisc/man/rcorrp.cens.html)

## Examples

``` r
m1 <- glm(vs ~ am + gear, data = mtcars, family = binomial)
m2 <- glm(vs ~ am + gear + wt, data = mtcars, family = binomial)
reclassificationJS(
  data = mtcars, cOutcome = 8,
  predrisk1 = predict(m1, type = "response"),
  predrisk2 = predict(m2, type = "response"), cutoff = c(0, .20, .40, 1)
)
#>                  value      95% CI       p
#> NRI(Categorical) 0.754 0.341-1.167 < 0.001
#> NRI(Continuous)  1.413 0.943-1.882 < 0.001
#> IDI              0.532 0.356-0.709 < 0.001
```
