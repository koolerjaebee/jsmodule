# logisticModule2: Shiny modulde server for logistic regression for reactive data.

Shiny modulde server for logistic regression for reactive data.

## Usage

``` r
logisticModule2(
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

  event variables as vector for logistic regression, Default: NULL

## Value

Shiny modulde server for logistic regression.

## Details

Shiny modulde server for logistic regression.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      regressModuleUI("logistic")
    ),
    mainPanel(
      DTOutput("logistictable")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_logistic <- callModule(logisticModule2, "logistic",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$logistictable <- renderDT({
    datatable(out_logistic()$table, rownames = T, caption = out_logistic()$caption)
  })
}
```
