# optionUI: Option UI with icon

Option UI with icon

## Usage

``` r
optionUI(id)
```

## Arguments

- id:

  id

## Value

Option UI with icon

## Details

Option UI with icon

## See also

[`dropdownButton`](https://dreamrs.github.io/shinyWidgets/reference/dropdownButton.html),[`tooltipOptions`](https://dreamrs.github.io/shinyWidgets/reference/tooltipOptions.html)

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
      optionUI("kaplan"),
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
