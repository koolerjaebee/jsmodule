# kaplanModule: shiny module server for kaplan-meier plot.

Shiny module server for kaplan-meier plot.

## Usage

``` r
kaplanModule(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  id.cluster = NULL,
  timeby = NULL,
  range.x = NULL,
  range.y = NULL,
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

  Reactive data

- data_label:

  Reactive data label

- data_varStruct:

  Reactive List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  Reactive survey data. default: NULL

- id.cluster:

  Reactive cluster variable if marginal model, Default: NULL

- timeby:

  timeby, Default: NULL

- range.x:

  range of x axis, Default: NULL

- range.y:

  range of y axis, Default: NULL

- vec.event:

  event variables as vector for survival analysis, Default: NULL

- vec.time:

  time variables as vector for survival analysis, Default: NULL

## Value

Shiny module server for kaplan-meier plot.

## Details

Shiny module server for kaplan-meier plot.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
library(ggplot2)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      kaplanUI("kaplan")
    ),
    mainPanel(
      plotOutput("kaplan_plot"),
      ggplotdownUI("kaplan")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_kaplan <- callModule(kaplanModule, "kaplan",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$kaplan_plot <- renderPlot({
    print(out_kaplan())
  })
}
```
