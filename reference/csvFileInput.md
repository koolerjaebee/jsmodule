# csvFileInput: Shiny module UI for file upload.

Shiny module UI for file upload supporting csv, xlsx, sav, sas7bdat, and
dta formats. It provides UI outputs for various data manipulation
options.

## Usage

``` r
csvFileInput(id, label = "Upload data (csv/xlsx/sav/sas7bdat/dta)")
```

## Arguments

- id:

  A string, the module id.

- label:

  A string, the label for the file input, Default: 'Upload data
  (csv/xlsx/sav/sas7bdat/dta)'

## Value

A Shiny UI object.

## Details

This function only defines the UI. The corresponding server function,
\`csvFile\`, handles the logic.

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(DT)
  library(jstable)

  ui <- fluidPage(
    sidebarLayout(
      sidebarPanel(
        csvFileInput("datafile")
      ),
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
    data_info <- callModule(csvFile, "datafile")

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
