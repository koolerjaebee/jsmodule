# ROC_table: extract AUC, NRI and IDI information from list of roc object in pROC packages.

extract AUC, NRI and IDI information from list of roc in pROC packages

## Usage

``` r
ROC_table(ListModel, dec.auc = 3, dec.p = 3)
```

## Arguments

- ListModel:

  list of roc object

- dec.auc:

  digits for AUC, Default: 3

- dec.p:

  digits for p value, Default: 3

## Value

table of AUC, NRI and IDI information

## Details

extract AUC, NRI and IDI information from list of roc object in pROC
packages.

## See also

[`ci.auc`](https://rdrr.io/pkg/pROC/man/ci.auc.html),[`roc.test`](https://rdrr.io/pkg/pROC/man/roc.test.html)
[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html),
[`rbindlist`](https://rdatatable.gitlab.io/data.table/reference/rbindlist.html)

## Examples

``` r
library(pROC)
#> Type 'citation("pROC")' for a citation.
#> 
#> Attaching package: ‘pROC’
#> The following objects are masked from ‘package:stats’:
#> 
#>     cov, smooth, var
m1 <- glm(vs ~ am + gear, data = mtcars, family = binomial)
m2 <- glm(vs ~ am + gear + wt, data = mtcars, family = binomial)
m3 <- glm(vs ~ am + gear + wt + mpg, data = mtcars, family = binomial)
roc1 <- roc(m1$y, predict(m1, type = "response"))
#> Setting levels: control = 0, case = 1
#> Setting direction: controls < cases
roc2 <- roc(m2$y, predict(m2, type = "response"))
#> Setting levels: control = 0, case = 1
#> Setting direction: controls < cases
roc3 <- roc(m3$y, predict(m3, type = "response"))
#> Setting levels: control = 0, case = 1
#> Setting direction: controls < cases
list.roc <- list(roc1, roc2, roc3)
ROC_table(list.roc)
#>    Prediction Model   AUC      95% CI P-value for AUC Difference   IDI
#>              <char> <num>      <char>                      <num> <num>
#> 1:          Model 1 0.635 0.437-0.833                         NA    NA
#> 2:          Model 2 0.929     0.836-1                      0.004 0.532
#> 3:          Model 3 0.944      0.87-1                      0.360 0.039
#>          95% CI P-value for IDI continuous NRI      95% CI P-value for NRI
#>          <char>          <char>          <num>      <char>          <char>
#> 1:         <NA>            <NA>             NA        <NA>            <NA>
#> 2:  0.356-0.709         < 0.001          1.413 0.943-1.882         < 0.001
#> 3: -0.024-0.102           0.223          0.540 -0.12-1.199           0.109
```
