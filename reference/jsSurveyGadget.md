# jsSurveyGadget: Shiny Gadget of survey data analysis.

Shiny Gadget including Data, Label info, Table 1, svyglm, Basic plot

## Usage

``` r
jsSurveyGadget(data, nfactor.limit = 20)
```

## Arguments

- data:

  data

- nfactor.limit:

  nlevels limit for categorical variables

## Value

Shiny Gadget including Data, Label info, Table 1, svyglm, Basic plot

## Details

Shiny Gadget including Data, Label info, Table 1, svyglm, Basic plot

## Examples

``` r
if (interactive()) {
  jsSurveyGadget(mtcars)
}
```
