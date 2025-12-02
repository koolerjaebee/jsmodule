# aiAssistantUI: AI Assistant module UI

AI-powered statistical analysis assistant module UI

## Usage

``` r
aiAssistantUI(id, show_api_config = TRUE)
```

## Arguments

- id:

  id

- show_api_config:

  If TRUE, shows API configuration UI. If FALSE, uses only env vars.
  Default: TRUE

## Value

AI Assistant module UI

## Details

Provides an interactive chat interface with AI for statistical analysis
code generation

## Examples

``` r
library(shiny)
library(DT)
library(survival)

ui <- fluidPage(
  fluidRow(
    column(12, aiAssistantUI("ai"))
  )
)

server <- function(input, output, session) {
  data <- reactive(colon)
  data.label <- reactive(jstable::mk.lev(colon))

  callModule(aiAssistant, "ai",
    data = data,
    data_label = data.label,
    data_varStruct = NULL,
    api_key = Sys.getenv("ANTHROPIC_API_KEY")
  )
}
```
