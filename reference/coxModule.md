# coxModule: shiny modulde server for Cox's model.

Shiny modulde server for Cox's model.

## Usage

``` r
coxModule(
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
  id.cluster = NULL,
  ties.coxph = "efron",
  vec.event = NULL,
  vec.time = NULL
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

  reactuve data label

- data_varStruct:

  reactive list of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  reactive survey data. default: NULL

- default.unires:

  Set default independent variables using univariate analysis.

- limit.unires:

  Change to default.unires = F if number of independent variables \>
  limit.unires, Default: 20

- id.cluster:

  reactive cluster variable if marginal cox model, Default: NULL

- ties.coxph:

  'coxph' ties option, one of 'efron', 'breslow', 'exact', default:
  'erfon'

- vec.event:

  event variables as vector for survival analysis, Default: NULL

- vec.time:

  time variables as vector for survival analysis, Default: NULL

## Value

Shiny modulde server for Cox's model.

## Details

Shiny modulde server for Cox's model.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      coxUI("cox")
    ),
    mainPanel(
      DTOutput("coxtable")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_cox <- callModule(coxModule, "cox",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$coxtable <- renderDT({
    datatable(out_cox()$table, rownames = T, caption = out_cox()$caption)
  })
}
```
