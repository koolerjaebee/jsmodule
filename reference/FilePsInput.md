# FilePsInput: Shiny module UI for propensity score analysis.

Provides a file input and UI outputs for options related to propensity
score matching.

## Usage

``` r
FilePsInput(id, label = "Upload data (csv/xlsx/sav/sas7bdat/dta)")
```

## Arguments

- id:

  A string, the module id.

- label:

  A string, the label for the file input.

## Value

A Shiny UI object.

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(DT)
  library(jstable)

  ui <- fluidPage(
    sidebarLayout(
      sidebarPanel(
        FilePsInput("datafile")
      ),
      mainPanel(
        tabsetPanel(
          type = "pills",
          tabPanel("Data", DTOutput("data")),
          tabPanel("Matching data", DTOutput("matdata")),
          tabPanel("Label", DTOutput("data_label"))
        )
      )
    )
  )

  server <- function(input, output, session) {
    mat_info <- callModule(FilePs, "datafile")

    output$data <- renderDT({ mat_info()$data })
    output$matdata <- renderDT({ mat_info()$matdata })
    output$data_label <- renderDT({ mat_info()$label })
  }
  shinyApp(ui, server)
}
```
