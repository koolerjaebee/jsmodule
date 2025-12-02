# timeROC_table: extract AUC information from list of timeROChelper object.

extract AUC information from list of timeROChelper object.

## Usage

``` r
timeROC_table(ListModel, dec.auc = 3, dec.p = 3)
```

## Arguments

- ListModel:

  list of timeROChelper object

- dec.auc:

  digits for AUC, Default: 3

- dec.p:

  digits for p value, Default: 3

## Value

table of AUC information

## Details

extract AUC information from list of timeROChelper object.

## See also

[`confint`](https://rdrr.io/r/stats/confint.html)
[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)

## Examples

``` r
# library(survival)
# list.timeROC <- lapply(list("age", c("age", "sex")),
#                      function(x){
#                        timeROChelper("status", "time", x, t = 365, data = lung)
#                       })
# timeROC_table(list.timeROC)
```
