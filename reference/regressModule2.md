# regressModule2: Shiny modulde server for linear regression for reactive data.

Shiny modulde server for linear regression for reactive data.

## Usage

``` r
regressModule2(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  default.unires = T,
  limit.unires = 20,
  vec.event = NULL
)
```

## Arguments

- input:

  input

- output:

  output

- session:

  session

- data:

  reactive data

- data_label:

  reactive data label

- data_varStruct:

  List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  reactive survey data. default: NULL

- default.unires:

  Set default independent variables using univariate analysis, Default:
  T

- limit.unires:

  Change to default.unires = F if number of independent variables \>
  limit.unires, Default: 20

- vec.event:

  event variables as vector for linear regression, Default: NULL

## Value

Shiny modulde server for linear regression.

## Details

Shiny modulde server for linear regression.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      regressModuleUI("linear")
    ),
    mainPanel(
      DTOutput("lineartable")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_linear <- callModule(regressModule2, "linear",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$lineartable <- renderDT({
    datatable(out_linear()$table, rownames = T, caption = out_linear()$caption)
  })
}
```
