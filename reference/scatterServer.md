# scatterServer: shiny module server for scatterplot.

Shiny module server for scatterplot.

## Usage

``` r
scatterServer(id, data, data_label, data_varStruct = NULL, nfactor.limit = 10)
```

## Arguments

- id:

  id

- data:

  Reactive data

- data_label:

  Reactive data label

- data_varStruct:

  Reactive List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

## Value

Shiny module server for scatterplot.

## Details

Shiny module server for scatterplot.

## Examples

``` r
library(shiny)
library(ggplot2)
library(ggpubr)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      scatterUI("scatter")
    ),
    mainPanel(
      optionUI("scatter"),
      plotOutput("scatter_plot"),
      ggplotdownUI("scatter")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_scatter <- scatterServer("scatter",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$scatter_plot <- renderPlot({
    print(out_scatter())
  })
}
```
