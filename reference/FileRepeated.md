# FileRepeated: Server for repeated measures analysis.

Server module for repeated measures analysis. It uses \`DataManager\`
and adds a control for selecting the repeated measures variable.

## Usage

``` r
FileRepeated(input, output, session, nfactor.limit = 20)
```

## Arguments

- input, output, session:

  Standard Shiny server parameters.

- nfactor.limit:

  An integer, the threshold for unique values.

## Value

A reactive list with the processed \`data\`, \`label\`, and \`id.gee\`.
