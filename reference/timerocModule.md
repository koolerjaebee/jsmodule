# timerocModule: shiny module server for time-dependent roc analysis

shiny module server for time-dependent roc analysis

shiny module server for time-dependent roc analysis- input number of
model as integer

## Usage

``` r
timerocModule(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  id.cluster = NULL,
  iid = TRUE,
  NRIIDI = TRUE
)

timerocModule2(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  id.cluster = NULL,
  iid = T,
  NRIIDI = T
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

  Reactuve data label

- data_varStruct:

  Reactive List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  Reactive survey data. default: NULL

- id.cluster:

  Reactive cluster variable if marginal model, Default: NULL

- iid:

  logical, get CI of AUC, Default: T

- NRIIDI:

  logical, get NRI & IDI, Default: T

## Value

shiny module server for time-dependent roc analysis

shiny module server for time dependent roc analysis- input number of
model as integer

## Details

shiny module server for time-dependent roc analysis

shiny module server for time dependent roc analysis- input number of
model as integer

## See also

[`quantile`](https://rdrr.io/r/stats/quantile.html)
[`setkey`](https://rdatatable.gitlab.io/data.table/reference/setkey.html)
[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)
[`rbindlist`](https://rdatatable.gitlab.io/data.table/reference/rbindlist.html)

[`quantile`](https://rdrr.io/r/stats/quantile.html)
[`setkey`](https://rdatatable.gitlab.io/data.table/reference/setkey.html)
[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)
[`rbindlist`](https://rdatatable.gitlab.io/data.table/reference/rbindlist.html)

## Examples

``` r
  library(shiny)
  library(DT)
  library(data.table)
  library(jstable)
  library(ggplot2)
  library(timeROC)
  library(survIDINRI)
#> Loading required package: survC1

  ui <- fluidPage(sidebarLayout(
    sidebarPanel(timerocUI("timeroc")),
    mainPanel(
      plotOutput("plot_timeroc"),
      ggplotdownUI("timeroc"),
      DTOutput("table_timeroc")
    )
  ))


  server <- function(input, output, session) {
    data <- reactive({
      dt_data <- as.data.table(pbc)

      factor_vars <- names(dt_data)[sapply(dt_data, function(x){length(table(x))}) <= 6]
      dt_data[, (factor_vars) := lapply(.SD, factor), .SDcols = factor_vars]

      return(dt_data)
    })

    data.label <- reactive({
      jstable::mk.lev(data())
    })

    out_timeroc <- callModule(
      timerocModule,
      "timeroc",
      data = data,
      data_label = data.label,
      data_varStruct = NULL
    )

    observe({
      tb <- tryCatch(out_timeroc()$tb, error = function(e) NULL)
      print(tb)
    })

    output$plot_timeroc <- renderPlot({
      {
        print(out_timeroc()$plot)
      }
    })


    output$table_timeroc <- renderDT({
      datatable(
        out_timeroc()$tb,
        rownames = F,
        editable = F,
        extensions = "Buttons",
        caption = "ROC results",
        options = c(jstable::opt.tbreg("roctable"), list(scrollX = TRUE))
      )
    })


  }


  library(shiny)
  library(DT)
  library(data.table)
  library(jstable)
  library(ggplot2)
  library(timeROC)
  library(survIDINRI)

  ui <- fluidPage(sidebarLayout(
    sidebarPanel(timerocUI("timeroc")),
    mainPanel(
      plotOutput("plot_timeroc"),
      ggplotdownUI("timeroc"),
      DTOutput("table_timeroc")
    )
  ))


  server <- function(input, output, session) {
    data <- reactive({
      dt_data <- as.data.table(pbc)

      factor_vars <- names(dt_data)[sapply(dt_data, function(x){length(table(x))}) <= 6]
      dt_data[, (factor_vars) := lapply(.SD, factor), .SDcols = factor_vars]

      return(dt_data)
    })

    data.label <- reactive({
      jstable::mk.lev(data())
    })

    out_timeroc <- callModule(
      timerocModule2,
      "timeroc",
      data = data,
      data_label = data.label,
      data_varStruct = NULL
    )

    observe({
      tb <- tryCatch(out_timeroc()$tb, error = function(e) NULL)
      print(tb)
    })

    output$plot_timeroc <- renderPlot({
      {
        print(out_timeroc()$plot)
      }
    })


    output$table_timeroc <- renderDT({
      datatable(
        out_timeroc()$tb,
        rownames = F,
        editable = F,
        extensions = "Buttons",
        caption = "ROC results",
        options = c(jstable::opt.tbreg("roctable"), list(scrollX = TRUE))
      )
    })


  }


```
