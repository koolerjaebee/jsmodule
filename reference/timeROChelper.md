# timeROChelper: Helper function for timerocModule

Helper function for timerocModule

## Usage

``` r
timeROChelper(
  var.event,
  var.time,
  vars.ind,
  t,
  data,
  design.survey = NULL,
  id.cluster = NULL
)
```

## Arguments

- var.event:

  event

- var.time:

  time

- vars.ind:

  independent variable

- t:

  time

- data:

  data

- design.survey:

  survey data, Default: NULL

- id.cluster:

  cluster variable if marginal model, Default: NULL

## Value

timeROC and coxph object

## Details

Helper function for timerocModule

## See also

[`coxph`](https://rdrr.io/pkg/survival/man/coxph.html)
[`svycoxph`](https://rdrr.io/pkg/survey/man/svycoxph.html)
[`predict`](https://rdrr.io/r/stats/predict.html)
[`timeROC`](https://rdrr.io/pkg/timeROC/man/timeROC.html)

## Examples

``` r
# library(survival)
# timeROChelper("status", "time", c("age", "sex"), t = 365, data = lung)
```
