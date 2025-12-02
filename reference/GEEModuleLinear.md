# GEEModuleLinear: shiny modulde server for gaussian generalized estimating equation(GEE) using reactive data.

Shiny modulde server for gaussian generalized estimating equation(GEE)
using reactive data.

## Usage

``` r
GEEModuleLinear(
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

  event variables as vector for gaussian generalized estimating
  equation(GEE), Default: NULL

## Value

Shiny modulde server for gaussian generalized estimating equation(GEE).

## Details

Shiny modulde server for gaussian generalized estimating equation(GEE)
using reactive data.

## Examples

``` r
library(shiny)
library(DT)
#> 
#> Attaching package: ‘DT’
#> The following objects are masked from ‘package:shiny’:
#> 
#>     dataTableOutput, renderDataTable
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      GEEModuleUI("linear")
    ),
    mainPanel(
      DTOutput("lineartable")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))
  id.gee <- reactive("mpg")

  out_linear <- callModule(GEEModuleLinear, "linear",
    data = data, data_label = data.label,
    data_varStruct = NULL, id.gee = id.gee
  )

  output$lineartable <- renderDT({
    hide <- which(colnames(out_linear()$table) == "sig")
    datatable(out_linear()$table,
      rownames = T, extension = "Buttons", caption = out_linear()$caption,
      options = c(
        opt.tbreg(out_linear()$caption),
        list(columnDefs = list(list(visible = FALSE, targets = hide))),
        list(scrollX = TRUE)
      )
    ) %>% formatStyle("sig", target = "row", backgroundColor = styleEqual("**", "yellow"))
  })
}
```
