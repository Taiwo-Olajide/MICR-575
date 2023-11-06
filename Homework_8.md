# Homework 8

# Joins

1.  Imagine you’ve found the top 10 most popular destinations using this
    code:

``` r
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ✔ ggplot2   3.4.4     ✔ tibble    3.2.1
    ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
    ✔ purrr     1.0.2     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(nycflights13)

top_dest <- flights |>
  count(dest, sort = TRUE) |>
  head(10)
```

How can you find all flights to those destinations?

## Answer

``` r
Topflight <- top_dest |>
  left_join(flights) |>
  select(dest, carrier, flight)

Topflight2 <- Topflight |>
  arrange(dest)
```

# Functions

2.  Write a function to ‘rescale’ a numeric vector by subtracting the
    mean of the vector from each element and then dividing each element
    by the standard deviation.

## Answer

``` r
series <- c(2,4,6,8,10,12)
series2 <- (series - mean(series))/ sd(series)
```
