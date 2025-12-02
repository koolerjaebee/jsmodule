# jsBasicGadget: Shiny Gadget of Basic Statistics in Medical Research.

Shiny Gadget including Data, Label info, Table 1, Regression(linear,
logistic), Basic plot

## Usage

``` r
jsBasicGadget(data, nfactor.limit = 20)
```

## Arguments

- data:

  data

- nfactor.limit:

  nlevels limit for categorical variables

## Value

Shiny Gadget including Data, Label info, Table 1, Regression(linear,
logistic), Basic plot

## Details

Shiny Gadget including Data, Label info, Table 1, Regression(linear,
logistic), Basic plot

## Examples

``` r
if (interactive()) {
  jsBasicGadget(mtcars)
}
```
