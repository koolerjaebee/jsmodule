# mklist: function to make variable list lncluding specific variables.

Function to make variable list lncluding specific variables.

## Usage

``` r
mklist(varlist, vars)
```

## Arguments

- varlist:

  Original variable list.

- vars:

  variable to include.

## Value

variable list lncluding specific variables.

## Details

Internal function

## Examples

``` r
data_varStruct <- list(variable = names(mtcars))
mklist(data_varStruct, names(mtcars))
#> $variable
#>  [1] "mpg"  "cyl"  "disp" "hp"   "drat" "wt"   "qsec" "vs"   "am"   "gear"
#> [11] "carb"
#> 
```
