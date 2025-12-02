# FileSurveyInput: UI for survey data analysis.

File upload UI for survey data analysis, with controls for survey design
elements.

## Usage

``` r
FileSurveyInput(id, label = "Upload data (csv/xlsx/sav/sas7bdat/dta)")
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
  library(survey)

  ui <- fluidPage(
    sidebarLayout(
      sidebarPanel(FileSurveyInput("datafile")),
      mainPanel(
        h4("Survey object details:"),
        verbatimTextOutput("survey_summary"),
        tabsetPanel(
          type = "pills",
          tabPanel("Data", DTOutput("data")),
          tabPanel("Label", DTOutput("data_label"))
        )
      )
    )
  )

  server <- function(input, output, session) {
    data_info <- callModule(FileSurvey, "datafile")
    output$data <- renderDT({
      data_info()$data
    })
    output$label <- renderDT({
      data_info()$label
    })
    output$survey_summary <- renderPrint({
      print(data_info()$survey)
    })
  }
  shinyApp(ui, server)
}
```
