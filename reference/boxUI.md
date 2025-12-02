# boxUI: shiny module UI for boxplot

Shiny module UI for boxplot

## Usage

``` r
boxUI(id, label = "boxplot")
```

## Arguments

- id:

  id

- label:

  label

## Value

Shiny module UI for boxplot

## Details

Shiny module UI for boxplot

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
