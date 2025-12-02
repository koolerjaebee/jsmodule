# jsRepeatedGadget: Shiny Gadget of Repeated measure analysis.

Shiny Gadget including Data, Label info, Table 1, GEE(linear, logistic),
Basic plot

## Usage

``` r
jsRepeatedGadget(data, nfactor.limit = 20)
```

## Arguments

- data:

  data

- nfactor.limit:

  nlevels limit for categorical variables

## Value

Shiny Gadget including Data, Label info, Table 1, GEE(linear, logistic),
Basic plot

## Details

Shiny Gadget including Data, Label info, Table 1, GEE(linear, logistic),
Basic plot

## Examples

``` r
if (interactive()) {
  jsRepeatedGadget(mtcars)
}
```
