p8105_hw1_jr4550
================
Sept 20, 2025

I’m an R Markdown document!

## Problem 1

### loading moderndive and early_january_weather dataset

``` r
library(moderndive)
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.2     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
data("early_january_weather")
```

### early_january_weather Description

Number of rows = 358

``` r
nrow(early_january_weather)
```

    ## [1] 358

Number of columns = 15

``` r
ncol(early_january_weather)
```

    ## [1] 15

The mean of the Temperature is 39.58212

``` r
mean(early_january_weather$temp)
```

    ## [1] 39.58212

Variable names and values

``` r
head(
early_january_weather)
```

    ## # A tibble: 6 × 15
    ##   origin  year month   day  hour  temp  dewp humid wind_dir wind_speed wind_gust
    ##   <chr>  <int> <int> <int> <int> <dbl> <dbl> <dbl>    <dbl>      <dbl>     <dbl>
    ## 1 EWR     2013     1     1     1  39.0  26.1  59.4      270      10.4         NA
    ## 2 EWR     2013     1     1     2  39.0  27.0  61.6      250       8.06        NA
    ## 3 EWR     2013     1     1     3  39.0  28.0  64.4      240      11.5         NA
    ## 4 EWR     2013     1     1     4  39.9  28.0  62.2      250      12.7         NA
    ## 5 EWR     2013     1     1     5  39.0  28.0  64.4      260      12.7         NA
    ## 6 EWR     2013     1     1     6  37.9  28.0  67.2      240      11.5         NA
    ## # ℹ 4 more variables: precip <dbl>, pressure <dbl>, visib <dbl>,
    ## #   time_hour <dttm>

``` r
write.csv(early_january_weather, "early_january_weather.csv", row.names = FALSE)
```

### Scatterplot

In the scatterplot, from January 1-23, 2013 we see that around January
10th humidity starts to increase. Average temperature during this time
was 39.58 fahrenheit.

``` r
ggplot(early_january_weather, aes(x = time_hour, y = temp, colour = humid)) + 
    geom_point()
```

![](template_files/figure-gfm/yx_scatter-1.png)<!-- -->

``` r
ggsave("temp_vs_time.png", width = 8, height = 5)
```

## Problem 2

### Create data frame

``` r
library(tidyverse)
```

``` r
example_df = tibble(
  vec_numeric = rnorm(10),
  vec_char = c("My", "name", "is", "Jeff", "and", "I", "am", "taking", "data", "science"),
  vec_logical = c(TRUE, TRUE, TRUE, FALSE,TRUE, TRUE, TRUE, FALSE,FALSE,FALSE),
  vec_factor = factor(c("male", "male", "trans", "female","trans", "male", "female", "female","female", "female"))
)
```

``` r
mean(pull(example_df, vec_numeric))
```

    ## [1] -0.01706102

``` r
mean(pull(example_df, vec_char))
```

    ## Warning in mean.default(pull(example_df, vec_char)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(example_df, vec_logical))
```

    ## [1] 0.6

``` r
mean(pull(example_df, vec_factor))
```

    ## Warning in mean.default(pull(example_df, vec_factor)): argument is not numeric
    ## or logical: returning NA

    ## [1] NA

### Converting Varibles to numeric

``` r
as.numeric(pull(example_df, vec_char))
```

    ## Warning: NAs introduced by coercion

    ##  [1] NA NA NA NA NA NA NA NA NA NA

``` r
as.numeric(pull(example_df, vec_logical))
```

    ##  [1] 1 1 1 0 1 1 1 0 0 0

``` r
as.numeric(pull(example_df, vec_factor))
```

    ##  [1] 2 2 3 1 3 2 1 1 1 1

``` r
mean(as.numeric(pull(example_df, vec_char)))
```

    ## Warning in mean(as.numeric(pull(example_df, vec_char))): NAs introduced by
    ## coercion

    ## [1] NA

``` r
mean(as.numeric(pull(example_df, vec_logical)))
```

    ## [1] 0.6

``` r
mean(as.numeric(pull(example_df, vec_factor)))
```

    ## [1] 1.7
