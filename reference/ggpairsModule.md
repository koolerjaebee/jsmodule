# ggpairsModule: shiny module server for basic/scatter plot.

Shiny module server for basic/scatter plot.

## Usage

``` r
ggpairsModule(
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

  data

- data_label:

  data label

- data_varStruct:

  List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit for categorical variables, Default: 20

## Value

Shiny module server for basic/scatter plot.

## Details

Shiny module server for basic/scatter plot.

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
  data <- mtcars
  data.label <- jstable::mk.lev(mtcars)

  out_ggpairs <- callModule(ggpairsModule, "ggpairs",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$kaplan_plot <- renderPlot({
    print(out_ggpairs())
  })
}
```
