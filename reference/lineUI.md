# lineUI: shiny module UI for lineplot

Shiny module UI for lineplot

## Usage

``` r
lineUI(id, label = "lineplot")
```

## Arguments

- id:

  id

- label:

  label

## Value

Shiny module UI for lineplot

## Details

Shiny module UI for lineplot

## Examples

``` r
library(shiny)
library(ggplot2)
library(ggpubr)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      lineUI("line")
    ),
    mainPanel(
      optionUI("line"),
      plotOutput("line_plot"),
      ggplotdownUI("line")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_line <- lineServer("line",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$line_plot <- renderPlot({
    print(out_line())
  })
}
```
