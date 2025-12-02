# timerocUI: shiny module UI for time-dependent roc analysis

Shiny module UI for time-dependent roc analysis

## Usage

``` r
timerocUI(id)
```

## Arguments

- id:

  id

## Value

Shiny module UI for time-dependent roc analysis

## Details

Shiny module UI for time-dependent roc analysis

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
library(ggplot2)
library(timeROC)
library(survIDINRI)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      timerocUI("timeroc")
    ),
    mainPanel(
      plotOutput("plot_timeroc"),
      ggplotdownUI("timeroc"),
      DTOutput("table_timeroc")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- jstable::mk.lev(mtcars)

  out_timeroc <- callModule(timerocModule, "timeroc",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$plot_timeroc <- renderPlot({
    print(out_timeroc()$plot)
  })

  output$table_timeroc <- renderDT({
    datatable(out_timeroc()$tb,
      rownames = F, editable = F, extensions = "Buttons",
      caption = "ROC results",
      options = c(jstable::opt.tbreg("roctable"), list(scrollX = TRUE))
    )
  })
}
```
