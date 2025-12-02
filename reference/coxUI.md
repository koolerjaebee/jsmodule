# coxUI: shiny modulde UI for Cox's model.

Shiny modulde UI for Cox's model.

## Usage

``` r
coxUI(id)
```

## Arguments

- id:

  id

## Value

coxUI

## Details

Shiny modulde UI for Cox's model.

## Examples

``` r
coxUI(1)
#> <div id="1-eventtime" class="shiny-html-output"></div>
#> <div class="form-group shiny-input-container">
#>   <div class="checkbox">
#>     <label>
#>       <input id="1-check_rangetime" type="checkbox" class="shiny-input-checkbox"/>
#>       <span>Choose time ranges</span>
#>     </label>
#>   </div>
#> </div>
#> <div class="form-group shiny-input-container">
#>   <div class="checkbox">
#>     <label>
#>       <input id="1-cmp_risk_check" type="checkbox" class="shiny-input-checkbox"/>
#>       <span>Competing Risk Analysis(Fine-Gray)</span>
#>     </label>
#>   </div>
#> </div>
#> <div id="1-cmp_eventtime" class="shiny-html-output"></div>
#> <div id="1-rangetime" class="shiny-html-output"></div>
#> <div id="1-indep" class="shiny-html-output"></div>
#> <div class="form-group shiny-input-container">
#>   <label class="control-label" id="1-decimal-label" for="1-decimal">Digits</label>
#>   <input class="js-range-slider" id="1-decimal" data-skin="shiny" data-min="1" data-max="4" data-from="2" data-step="1" data-grid="true" data-grid-num="3" data-grid-snap="false" data-prettify-separator="," data-prettify-enabled="true" data-keyboard="true" data-data-type="number"/>
#> </div>
#> <div class="form-group shiny-input-container">
#>   <div class="checkbox">
#>     <label>
#>       <input id="1-subcheck" type="checkbox" class="shiny-input-checkbox"/>
#>       <span>Sub-group analysis</span>
#>     </label>
#>   </div>
#> </div>
#> <div id="1-subvar" class="shiny-html-output"></div>
#> <div id="1-subval" class="shiny-html-output"></div>
#> <div class="form-group shiny-input-container">
#>   <div class="checkbox">
#>     <label>
#>       <input id="1-step_check" type="checkbox" class="shiny-input-checkbox"/>
#>       <span>Stepwise variable selection</span>
#>     </label>
#>   </div>
#> </div>
#> <div id="1-step_direction" class="shiny-html-output"></div>
#> <div id="1-step_scope" class="shiny-html-output"></div>
```
