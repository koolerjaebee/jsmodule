# ggpairsModule2: shiny module server for basic/scatter plot for reactive data.

Shiny module server for basic/scatter plot for reactive data.

## Usage

``` r
ggpairsModule2(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 20
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

  List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit for categorical variables, Default: 20

## Value

Shiny module server for basic/scatter plot

## Details

Shiny module server for basic/scatter plot for reactive data.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
library(ggplot2)
library(GGally)

ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      ggpairsModuleUI1("ggpairs")
    ),
    mainPanel(
      plotOutput("ggpairs_plot"),
      ggpairsModuleUI2("ggpairs")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_ggpairs <- callModule(ggpairsModule2, "ggpairs",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$kaplan_plot <- renderPlot({
    print(out_ggpairs())
  })
}
```
