# jsPropensityGadget: Shiny Gadget for propensity score analysis.

Shiny Gadget including original/matching/IPTW data, Label info, Table 1,
Cox model, Basic/kaplan-meier plot.

## Usage

``` r
jsPropensityGadget(data, nfactor.limit = 20)
```

## Arguments

- data:

  data

- nfactor.limit:

  nlevels limit for categorical variables, Default: 20

## Value

Shiny Gadget including original/matching/IPTW data, Label info, Table 1,
Cox model, Basic/kaplan-meier plot.

## Details

Shiny Gadget including original/matching/IPTW data, Label info, Table 1,
Cox model, Basic/kaplan-meier plot.

## See also

[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)
[`matchit`](https://kosukeimai.github.io/MatchIt/reference/matchit.html),[`match.data`](https://kosukeimai.github.io/MatchIt/reference/match_data.html)
[`cox2.display`](https://jinseob2kim.github.io/jstable/reference/cox2.display.html),[`svycox.display`](https://jinseob2kim.github.io/jstable/reference/svycox.display.html)
[`survfit`](https://rdrr.io/pkg/survival/man/survfit.html),[`coxph`](https://rdrr.io/pkg/survival/man/coxph.html),[`Surv`](https://rdrr.io/pkg/survival/man/Surv.html)
[`jskm`](https://jinseob2kim.github.io/jskm/reference/jskm.html),[`svyjskm`](https://jinseob2kim.github.io/jskm/reference/svyjskm.html)
[`ggsave`](https://ggplot2.tidyverse.org/reference/ggsave.html)
[`svykm`](https://rdrr.io/pkg/survey/man/svykm.html)

## Examples

``` r
if (interactive()) {
  jsPropensityGadget(mtcars)
}
```
