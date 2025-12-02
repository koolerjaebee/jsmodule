# forestcoxServer:shiny module server for forestcox

Shiny module server for forestcox

## Usage

``` r
forestcoxServer(
  id,
  data,
  data_label,
  data_varStruct = NULL,
  nfactor.limit = 10,
  design.survey = NULL,
  cluster_id = NULL,
  vec.event = NULL,
  vec.time = NULL
)
```

## Arguments

- id:

  id

- data:

  Reactive data

- data_label:

  Reactive data label

- data_varStruct:

  Reactive List of variable structure, Default: NULL

- nfactor.limit:

  nlevels limit in factor variable, Default: 10

- design.survey:

  reactive survey data. default: NULL

- cluster_id:

  cluster option variable for marginal cox model

- vec.event:

  event variables as vector for survival analysis, Default: NULL

- vec.time:

  time variables as vector for survival analysis, Default: NULL

## Value

Shiny module server for forestcox

## Details

Shiny module server for forestcox

## See also

[`data.table-package`](https://rdatatable.gitlab.io/data.table/reference/data.table.html),
[`setDT`](https://rdatatable.gitlab.io/data.table/reference/setDT.html),
[`setattr`](https://rdatatable.gitlab.io/data.table/reference/setattr.html)
[`TableSubgroupMultiCox`](https://jinseob2kim.github.io/jstable/reference/TableSubgroupMultiCox.html)
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

library(shiny)
library(DT)
mtcars$vs <- factor(mtcars$vs)
mtcars$am <- factor(mtcars$am)
mtcars$kk <- factor(as.integer(mtcars$disp >= 150))
mtcars$kk1 <- factor(as.integer(mtcars$disp >= 200))

out <- mtcars
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      forestcoxUI("Forest")
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


server <- function(input, output, session) {
  data <- reactive(out)
  label <- reactive(jstable::mk.lev(out))
  outtable <- forestcoxServer("Forest", data = data, data_label = label)
  output$tablesub <- renderDT({
    outtable()[[1]]
  })
  output$forestplot <- renderPlot({
    a
    outtable()[[2]]
  })
}
```
