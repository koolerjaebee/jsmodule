# FilePs: Shiny module Server for propensity score analysis.

Server-side logic for propensity score analysis. It uses \`DataManager\`
for common data tasks and adds specific controls and calculations for
propensity score matching.

## Usage

``` r
FilePs(input, output, session, nfactor.limit = 20)
```

## Arguments

- input, output, session:

  Standard Shiny server parameters.

- nfactor.limit:

  An integer, the threshold for unique values.

## Value

A reactive expression returning a list with matched data and other
information.
