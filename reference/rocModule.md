# rocModule: shiny module server for roc analysis

shiny module server for roc analysis

## Usage

``` r
rocModule(
  input,
  output,
  session,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  id.cluster = NULL
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

## Value

shiny module server for roc analysis

## Details

shiny module server for roc analysis

## See also

[`quantile`](https://rdrr.io/r/stats/quantile.html)
[`setkey`](https://rdatatable.gitlab.io/data.table/reference/setkey.html)
[`ggroc`](https://rdrr.io/pkg/pROC/man/ggroc.html)
[`geeglm`](https://rdrr.io/pkg/geepack/man/geeglm.html)
[`svyglm`](https://rdrr.io/pkg/survey/man/svyglm.html)
[`theme_modern`](https://easystats.github.io/see/reference/theme_modern.html)

## Examples

``` r
library(shiny)
library(DT)
library(data.table)
library(jstable)
library(ggplot2)
library(pROC)
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      rocUI("roc")
    ),
    mainPanel(
      plotOutput("plot_roc"),
      tableOutput("cut_roc"),
      ggplotdownUI("roc"),
      DTOutput("table_roc")
    )
  )
)

server <- function(input, output, session) {
  data <- reactive(mtcars)
  data.label <- reactive(jstable::mk.lev(data1))

  out_roc <- callModule(rocModule, "roc",
    data = data, data_label = data.label,
    data_varStruct = NULL
  )

  output$plot_roc <- renderPlot({
    print(out_roc()$plot)
  })

  output$cut_roc <- renderTable({
    if (is.null(out_roc()$cut)) return(NULL)
    print(out_roc()$cut)
  })

  output$table_roc <- renderDT({
    datatable(out_roc()$tb,
      rownames = F, editable = F, extensions = "Buttons",
      caption = "ROC results",
      options = c(jstable::opt.tbreg("roctable"), list(scrollX = TRUE))
    )
  })
}
```
