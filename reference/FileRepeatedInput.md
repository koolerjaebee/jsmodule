# FileRepeatedInput: UI for repeated measures analysis.

File upload UI for repeated measure analysis.

## Usage

``` r
FileRepeatedInput(id, label = "Upload data (csv/xlsx/sav/sas7bdat/dta)")
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
      sidebarPanel(FileRepeatedInput("datafile")),
      mainPanel(
        tabsetPanel(
          type = "pills",
          tabPanel("Data", DTOutput("data")),
          tabPanel("Label", DTOutput("data_label"))
        )
      )
    )
  )

  server <- function(input, output, session) {
    data_info <- callModule(FileRepeated, "datafile")
    output$data <- renderDT({
      data_info()$data
    })
    output$label <- renderDT({
      data_info()$label
    })
  }
  shinyApp(ui, server)
}
```
