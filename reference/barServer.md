# barServer: shiny module server for barplot.

Shiny module server for barplot.

## Usage

``` r
barServer(id, data, data_label, data_varStruct = NULL, nfactor.limit = 10)
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

Shiny module server for barplot.

## Details

Shiny module server for barplot.

## Examples

``` r
library(shiny)
library(ggplot2)
library(ggpubr)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      barUI("bar")
    ),
    mainPanel(
      optionUI("bar"),
      plotOutput("bar_plot"),
      ggplotdownUI("bar")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_bar <- barServer("bar",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$bar_plot <- renderPlot({
    print(out_bar())
  })
}
```
