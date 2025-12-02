# Include jsmodule CSS styling

Adds the custom \`style.css\` file bundled with the jsmodule package to
a Shiny UI. This allows consistent styling (e.g., bold navbar title,
font tweaks, spacing) across all Shiny applications using this package.

## Usage

``` r
use_jsmodule_style()
```

## Value

An HTML \`\<link\>\` tag that loads the CSS into a Shiny UI

## Details

This function is meant to be used inside the UI of a Shiny app. It
automatically locates and includes the \`style.css\` file found in
\`inst/assets/\` of the jsmodule package installation.

## See also

[`include`](https://rstudio.github.io/htmltools/reference/include.html)

## Examples

``` r
if (FALSE) { # \dontrun{
use_jsmodule_style()
} # }
```
