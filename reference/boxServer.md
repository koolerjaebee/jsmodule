# boxServer: shiny module server for boxplot.

Shiny module server for boxplot.

## Usage

``` r
boxServer(id, data, data_label, data_varStruct = NULL, nfactor.limit = 10)
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

Shiny module server for boxplot.

## Details

Shiny module server for boxplot.

## Examples

``` r
library(shiny)
library(ggplot2)
library(ggpubr)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      boxUI("box")
    ),
    mainPanel(
      optionUI("box"),
      plotOutput("box_plot"),
      ggplotdownUI("box")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_box <- boxServer("box",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$box_plot <- renderPlot({
    print(out_box())
  })
}
```
