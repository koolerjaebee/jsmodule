# mksetdiff: function to make variable list excluding specific variables.

Function to make variable list excluding specific variables.

## Usage

``` r
mksetdiff(varlist, vars)
```

## Arguments

- varlist:

  Original variable list

- vars:

  variable to exclude.

## Value

variable list excluding specific variables.

## Details

Internal function

## Examples

``` r
data_varStruct <- list(variable = names(mtcars))
mksetdiff(data_varStruct, "mpg")
#> $variable
#>  [1] "cyl"  "disp" "hp"   "drat" "wt"   "qsec" "vs"   "am"   "gear" "carb"
#> 
```
