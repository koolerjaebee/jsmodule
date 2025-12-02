# scatterUI: shiny module UI for scatterplot

Shiny module UI for scatterplot

## Usage

``` r
scatterUI(id, label = "scatterplot")
```

## Arguments

- id:

  id

- label:

  label

## Value

Shiny module UI for scatterplot

## Details

Shiny module UI for scatterplot

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
