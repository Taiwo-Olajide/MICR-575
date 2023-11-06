# Homework 8

# Joins

1.  Imagine you’ve found the top 10 most popular destinations using this
    code:

``` r
library(tidyverse)

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
