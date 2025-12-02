# FileSurvey: Server for survey data analysis.

Server module for survey data analysis. It uses \`DataManager\` and adds
controls and logic for creating a \`survey.design\` object.

## Usage

``` r
FileSurvey(input, output, session, nfactor.limit = 20)
```

## Arguments

- input, output, session:

  Standard Shiny server parameters.

- nfactor.limit:

  An integer, the threshold for unique values.

## Value

A reactive list with \`data\`, \`label\`, \`naomit\`, and the \`survey\`
object.
