# lineServer: shiny module server for lineplot.

Shiny module server for lineplot.

## Usage

``` r
lineServer(id, data, data_label, data_varStruct = NULL, nfactor.limit = 10)
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

Shiny module server for lineplot.

## Details

Shiny module server for lineplot.

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
