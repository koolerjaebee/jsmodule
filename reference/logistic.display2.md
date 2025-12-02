# logistic.display2: Modified epiDisplay's logistic.display function.

Modified epiDisplay's logistic.display function for reactive data.

## Usage

``` r
logistic.display2(
  logistic.model,
  alpha = 0.05,
  crude = TRUE,
  crude.p.value = FALSE,
  decimal = 2,
  simplified = FALSE
)
```

## Arguments

- logistic.model:

  glm object(binomial)

- alpha:

  alpha, Default: 0.05

- crude:

  crude, Default: TRUE

- crude.p.value:

  crude.p.value, Default: FALSE

- decimal:

  decimal, Default: 2

- simplified:

  simplified, Default: FALSE

## Value

logistic table

## Details

Modified epiDisplay's logistic.display function for reactive data.

## Examples

``` r
model1 <- glm(am ~ cyl + disp, data = mtcars, family = binomial)
logistic.display2(model1, crude = TRUE, crude.p.value = TRUE, decimal = 3)
#> 
#> Logistic regression predicting am 
#>  
#>                   crude OR(95%CI)      crude P value adj. OR(95%CI)      
#> cyl (cont. var.)  0.501 (0.305,0.824)  0.0064        2.102 (0.514,8.604) 
#>                                                                          
#> disp (cont. var.) 0.986 (0.976,0.996)  0.0047        0.973 (0.946,1.001) 
#>                                                                          
#>                   P(Wald's test) P(LR-test)
#> cyl (cont. var.)  0.3015         0.2845    
#>                                            
#> disp (cont. var.) 0.0558         0.0205    
#>                                            
#> Log-likelihood = -14.29311
#> No. of observations = 32
#> AIC value = 34.58622
#> 
```
