# csvFile: Shiny module Server for file upload.

The server-side logic for the \`csvFileInput\` module. It uses the
\`DataManager\` R6 class to handle all data processing.

## Usage

``` r
csvFile(input, output, session, nfactor.limit = 20)
```

## Arguments

- input, output, session:

  Standard Shiny server parameters.

- nfactor.limit:

  An integer, the threshold for unique values to suggest a numeric
  variable as categorical, Default: 20

## Value

A reactive expression that returns a list with two elements: \`data\`
(the processed data.table) and \`label\` (a data.table with variable
label information).
