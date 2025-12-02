# survIDINRI_helper: Helper function for IDI.INF.OUT in survIDINRI packages

Helper function for IDI.INF.OUT in survIDINRI packages

## Usage

``` r
survIDINRI_helper(
  var.event,
  var.time,
  list.vars.ind,
  t,
  data,
  dec.auc = 3,
  dec.p = 3,
  id.cluster = NULL
)
```

## Arguments

- var.event:

  event

- var.time:

  time

- list.vars.ind:

  list of independent variable

- t:

  time

- data:

  data

- dec.auc:

  digits for AUC, Default: 3

- dec.p:

  digits for p value, Default: 3

- id.cluster:

  cluster variable if marginal model, Default: NULL

## Value

IDI, NRI

## Details

Helper function for IDI.INF.OUT in survIDINRI packages

## See also

[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)
[`model.matrix`](https://rdrr.io/r/stats/model.matrix.html)
[`coxph`](https://rdrr.io/pkg/survival/man/coxph.html)
[`Surv`](https://rdrr.io/pkg/survival/man/Surv.html)
[`IDI.INF.OUT`](https://rdrr.io/pkg/survIDINRI/man/IDI.INF.OUT.html)
[`IDI.INF`](https://rdrr.io/pkg/survIDINRI/man/IDI.INF.html)

## Examples

``` r
# library(survival)
# survIDINRI_helper("status", "time", list.vars.ind = list("age", c("age", "sex")),
#                  t = 365, data = lung)
```
