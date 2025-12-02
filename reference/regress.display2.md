# regress.display2: modified epiDisplay's regress.display function

regress.display function for reactive data

## Usage

``` r
regress.display2(
  regress.model,
  alpha = 0.05,
  crude = FALSE,
  crude.p.value = FALSE,
  decimal = 2,
  simplified = FALSE
)
```

## Arguments

- regress.model:

  lm object

- alpha:

  alpha, Default: 0.05

- crude:

  crude, Default: FALSE

- crude.p.value:

  crude.p.value, Default: FALSE

- decimal:

  decimal, Default: 2

- simplified:

  simplified, Default: FALSE

## Value

regress table

## Details

regress.display function for reactive data

## Examples

``` r
model1 <- glm(mpg ~ cyl + disp + vs, data = mtcars)
regress.display2(model1, crude = TRUE, crude.p.value = TRUE, decimal = 3)
#> Linear regression predicting mpg
#>  
#>                   crude coeff.(95%CI)     crude P value adj. coeff.(95%CI)   
#> cyl (cont. var.)  -2.876 (-3.534,-2.217)  < 0.001       -1.75 (-3.537,0.037) 
#>                                                                              
#> disp (cont. var.) -0.041 (-0.051,-0.032)  < 0.001       -0.02 (-0.042,0.001) 
#>                                                                              
#> vs: 1 vs 0        7.94 (4.607,11.274)     < 0.001       -0.634 (-4.517,3.25) 
#>                                                                              
#>                   P(t-test) P(F-test)
#> cyl (cont. var.)  0.0545    < 0.001  
#>                                      
#> disp (cont. var.) 0.0624    0.0581   
#>                                      
#> vs: 1 vs 0        0.7407    0.7407   
#>                                      
#> Log-likelihood = -79.5091
#> No. of observations = 32
#> AIC value = 169.01821
#> 
```
