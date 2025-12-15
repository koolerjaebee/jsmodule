# Safe evaluation wrapper with environment-aware security

Safe evaluation wrapper with environment-aware security

## Usage

``` r
safe_eval_expr(expr, envir, timeout = 10)
```

## Arguments

- expr:

  Expression to evaluate

- envir:

  Environment for evaluation

- timeout:

  Timeout in seconds (default: 10)

## Value

Evaluation result

## Details

In production mode, uses RAppArmor::eval.secure if available. In
development mode, uses standard eval for easier debugging.
