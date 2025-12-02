# GEEModuleLogistic: shiny modulde server for binomial gaussian generalized estimating equation(GEE) using reactive data.

Shiny modulde server for binomial gaussian generalized estimating
equation(GEE) using reactive data.

## Usage

``` r
GEEModuleLogistic(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  id.gee,
  vec.event = NULL
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

  reactive data, ordered by id.

- data_label:

  reactive data label

- data_varStruct:

  List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- id.gee:

  reactive repeated measure variable

- vec.event:

  event variables as vector for binomial gaussian generalized estimating
  equation(GEE), Default: NULL

## Value

Shiny modulde server for binomial gaussian generalized estimating
equation(GEE).

## Details

Shiny modulde server for binomial gaussian generalized estimating
equation(GEE) using reactive data.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      GEEModuleUI("logistic")
    ),
    mainPanel(
      DTOutput("logistictable")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))
  id.gee <- reactive("mpg")

  out_logistic <- callModule(GEEModuleLogistic, "logistic",
    data = data, data_label = data.label,
    data_varStruct = NULL, id.gee = id.gee
  )

  output$logistictable <- renderDT({
    hide <- which(colnames(out_logistic()$table) == "sig")
    datatable(out_logistic()$table,
      rownames = T, extension = "Buttons",
      caption = out_logistic()$caption,
      options = c(
        opt.tbreg(out_logistic()$caption),
        list(columnDefs = list(list(visible = FALSE, targets = hide))),
        list(scrollX = TRUE)
      )
    ) %>% formatStyle("sig", target = "row", backgroundColor = styleEqual("**", "yellow"))
  })
}
```
