# forestglmServer:shiny module server for forestglm

Shiny module server for forestglm

## Usage

``` r
forestglmServer(
  id,
  data,
  data_label,
  family,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  repeated_id = NULL
)
```

## Arguments

- id:

  id

- data:

  Reactive data

- data_label:

  Reactive data label

- family:

  family, "gaussian" or "binomial" or 'poisson' or 'quasipoisson'

- data_varStruct:

  Reactive List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  reactive survey data. default: NULL

- repeated_id:

  data when repeated id. default: F

## Value

Shiny module server for forestglm

## Details

Shiny module server for forestglm

## See also

[`TableSubgroupMultiGLM`](https://jinseob2kim.github.io/jstable/reference/TableSubgroupMultiGLM.html)
[`data.table-package`](https://rdatatable.gitlab.io/data.table/reference/data.table.html),[`setDT`](https://rdatatable.gitlab.io/data.table/reference/setDT.html),
[`setattr`](https://rdatatable.gitlab.io/data.table/reference/setattr.html)
[`cor`](https://rdrr.io/r/stats/cor.html),
[`coef`](https://rdrr.io/r/stats/coef.html) `surveysummary`,
[`svytable`](https://rdrr.io/pkg/survey/man/svychisq.html)
[`forest_theme`](https://rdrr.io/pkg/forestploter/man/forest_theme.html),
[`forest`](https://rdrr.io/pkg/forestploter/man/forest.html)
[`dml`](https://davidgohel.github.io/rvg/reference/dml.html)
[`read_pptx`](https://davidgohel.github.io/officer/reference/read_pptx.html),
[`add_slide`](https://davidgohel.github.io/officer/reference/add_slide.html),
[`ph_with`](https://davidgohel.github.io/officer/reference/ph_with.html),
[`ph_location`](https://davidgohel.github.io/officer/reference/ph_location.html)

## Examples

``` r
library(shiny)
library(DT)
mtcars$vs <- factor(mtcars$vs)
mtcars$am <- factor(mtcars$am)
mtcars$kk <- factor(as.integer(mtcars$disp >= 150))
mtcars$kk1 <- factor(as.integer(mtcars$disp >= 200))

ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      forestglmUI("Forest")
    ),
    mainPanel(
      tabsetPanel(
        type = "pills",
        tabPanel(
          title = "Data",
          DTOutput("tablesub"),
        ),
        tabPanel(
          title = "figure",
          plotOutput("forestplot", width = "100%"),
          ggplotdownUI("Forest")
        )
      )
    )
  )
)

out <- mtcars

server <- function(input, output, session) {
  data <- reactive(out)
  label <- reactive(jstable::mk.lev(out))
  outtable <- forestglmServer("Forest", data = data, data_label = label, family = "binomial")
  output$tablesub <- renderDT({
    outtable()[[1]]
  })
  output$forestplot <- renderPlot({
    outtable()[[2]]
  })
}
```
