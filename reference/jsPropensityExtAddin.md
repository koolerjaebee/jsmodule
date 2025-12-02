# jsPropensityExtAddin: RStudio Addin for propensity score analysis with external data.

RStudio Addin for propensity score analysis with external
csv/xlsx/sas7bdat/sav/dta file.

## Usage

``` r
jsPropensityExtAddin(nfactor.limit = 20, max.filesize = 2048)
```

## Arguments

- nfactor.limit:

  nlevels limit for categorical variables, Default: 20

- max.filesize:

  Maximum file size to upload (MB), Default: 2048 (2 GB)

## Value

RStudio Addin for propensity score analysis with external data.

## Details

RStudio Addin for propensity score analysis with external
csv/xlsx/sas7bdat/sav/dta file.

## See also

[`pbc`](https://rdrr.io/pkg/survival/man/pbc.html)
[`fwrite`](https://rdatatable.gitlab.io/data.table/reference/fwrite.html),[`data.table`](https://rdatatable.gitlab.io/data.table/reference/data.table.html)
[`svydesign`](https://rdrr.io/pkg/survey/man/svydesign.html)
[`opt.tbreg`](https://jinseob2kim.github.io/jstable/reference/opt.tbreg.html)

## Examples

``` r
if (interactive()) {
  jsPropensityExtAddin()
}
```
