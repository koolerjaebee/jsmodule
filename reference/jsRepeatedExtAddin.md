# jsRepeatedExtAddin: RStudio Addin for repeated measure analysis with external data.

RStudio Addin for repeated measure analysis with external
csv/xlsx/sas7bdat/sav/dta file.

## Usage

``` r
jsRepeatedExtAddin(nfactor.limit = 20, max.filesize = 2048)
```

## Arguments

- nfactor.limit:

  nlevels limit for categorical variables, Default: 20

- max.filesize:

  Maximum file size to upload (MB), Default: 2048 (2 GB)

## Value

RStudio Addin for repeated measure analysis with external data.

## Details

RStudio Addin for repeated measure analysis with external
csv/xlsx/sas7bdat/sav/dta file.

## See also

[`fwrite`](https://rdatatable.gitlab.io/data.table/reference/fwrite.html)
[`colon`](https://rdrr.io/pkg/survival/man/colon.html)
[`opt.tbreg`](https://jinseob2kim.github.io/jstable/reference/opt.tbreg.html)

## Examples

``` r
if (interactive()) {
  jsRepeatedExtAddin()
}
```
