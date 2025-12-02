# aiAssistant: AI Assistant module server

AI-powered statistical analysis assistant module server

## Usage

``` r
aiAssistant(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  api_key = NULL,
  stats_guide = NULL,
  show_api_config = TRUE,
  analysis_context = NULL
)
```

## Arguments

- input:

  input

- output:

  output

- session:

  session

- data:

  Data (reactive)

- data_label:

  Data label (reactive)

- data_varStruct:

  Variable structure list of data, Default: NULL

- api_key:

  API key for AI service. If NULL, reads from provider-specific env var

- stats_guide:

  Optional custom statistical guide text. If NULL, uses default guide

- show_api_config:

  If TRUE, shows API config UI. If FALSE, uses only env vars. Default:
  TRUE

- analysis_context:

  Optional reactive or list containing previous analysis results. AI can
  reference these when user asks follow-up questions. Default: NULL

## Value

AI Assistant module server

## Details

Provides interactive statistical analysis code generation using AI

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
