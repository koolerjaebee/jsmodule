# aiAssistantUI: AI Assistant module UI

AI-powered statistical analysis assistant module UI

## Usage

``` r
aiAssistantUI(id, show_api_config = TRUE)
```

## Arguments

- id:

  Module's namespace ID. Used to create unique identifiers for UI
  elements.

- show_api_config:

  If TRUE, shows API configuration UI. If FALSE, uses only env vars.
  Default: TRUE

## Value

Shiny UI tagList containing the AI Assistant interface with chat, code
editor, and result panels

## Details

Provides an interactive chat interface with AI for statistical analysis
code generation

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup: Add API key to .Renviron file
# usethis::edit_r_environ()
# Add line: ANTHROPIC_API_KEY=your_actual_key_here
# Save and restart R

library(shiny)
library(DT)
library(survival)

# Example 1: Basic usage with auto-generated variable structure
ui <- fluidPage(
  titlePanel("AI Statistical Assistant"),
  aiAssistantUI("ai")
)

server <- function(input, output, session) {
  data <- reactive(colon)
  data.label <- reactive(jstable::mk.lev(colon))

  callModule(aiAssistant, "ai",
    data = data,
    data_label = data.label,
    data_varStruct = NULL  # Auto-generates variable structure
  )
}

shinyApp(ui, server)

# Example 2: With custom variable structure and analysis context
ui2 <- fluidPage(
  titlePanel("Survival Analysis Assistant"),
  aiAssistantUI("ai")
)

server2 <- function(input, output, session) {
  data <- reactive(colon)
  data.label <- reactive(jstable::mk.lev(colon))

  # Custom variable structure for survival analysis
  var_struct <- reactive({
    list(
      variable = names(colon),
      Base = c("rx", "sex", "age", "obstruct", "nodes"),
      Event = "status",
      Time = "time"
    )
  })

  callModule(aiAssistant, "ai",
    data = data,
    data_label = data.label,
    data_varStruct = var_struct,
    analysis_context = reactive({
      "Colon cancer adjuvant chemotherapy trial (survival::colon).
       Primary outcome: time to recurrence or death (status/time).
       Treatment groups: Observation, Levamisole, Levamisole+5-FU."
    })
  )
}

shinyApp(ui2, server2)

# Example 3: Production deployment without API config UI
ui_prod <- fluidPage(
  aiAssistantUI("ai", show_api_config = FALSE)
)

server_prod <- function(input, output, session) {
  # Relies entirely on .Renviron configuration
  callModule(aiAssistant, "ai",
    data = reactive(mtcars),
    data_label = reactive(jstable::mk.lev(mtcars)),
    show_api_config = FALSE
  )
}

shinyApp(ui_prod, server_prod)
} # }
```
