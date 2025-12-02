# tb1module2: table 1 shiny module server for reactive data.

Table 1 shiny module server for descriptive statistics for reactive
data.

## Usage

``` r
tb1module2(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  showAllLevels = T,
  argsExact = list(workspace = 2 * 10^7, simulate.p.value = T)
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

  Reactive data

- data_label:

  Reactive data label

- data_varStruct:

  Variable structure list of data, Default: NULL

- nfactor.limit:

  maximum factor levels to include, Default: 10

- design.survey:

  Reactive survey data of survey package. Default: NULL

- showAllLevels:

  Show All label information with 2 categorical variables, Default: T

- argsExact:

  Option for Fisher exact test memory limit.

## Value

Table 1 shiny module server for descriptive statistics.

## Details

Table 1 shiny module server for descriptive statistics.

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      tb1moduleUI("tb1")
    ),
    mainPanel(
      DTOutput("table1")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(mtcars))

  out_tb1 <- callModule(tb1module2, "tb1",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$table1 <- renderDT({
    tb <- out_tb1()$table
    cap <- out_tb1()$caption
    out.tb1 <- datatable(tb, rownames = T, extension = "Buttons", caption = cap)
    return(out.tb1)
  })
}
```
