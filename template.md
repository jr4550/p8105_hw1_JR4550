p8105_hw1_jr4550
================
Sept 20, 2025

I’m an R Markdown document!

## Problem 1

\#loading moderndive

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

\#early_january_weather Description

Number of rows 358  
Number of columns 15 The mean of the Temperature is 39.58212

``` r
early_january_weather
```

    ## # A tibble: 358 × 15
    ##    origin  year month   day  hour  temp  dewp humid wind_dir wind_speed
    ##    <chr>  <int> <int> <int> <int> <dbl> <dbl> <dbl>    <dbl>      <dbl>
    ##  1 EWR     2013     1     1     1  39.0  26.1  59.4      270      10.4 
    ##  2 EWR     2013     1     1     2  39.0  27.0  61.6      250       8.06
    ##  3 EWR     2013     1     1     3  39.0  28.0  64.4      240      11.5 
    ##  4 EWR     2013     1     1     4  39.9  28.0  62.2      250      12.7 
    ##  5 EWR     2013     1     1     5  39.0  28.0  64.4      260      12.7 
    ##  6 EWR     2013     1     1     6  37.9  28.0  67.2      240      11.5 
    ##  7 EWR     2013     1     1     7  39.0  28.0  64.4      240      15.0 
    ##  8 EWR     2013     1     1     8  39.9  28.0  62.2      250      10.4 
    ##  9 EWR     2013     1     1     9  39.9  28.0  62.2      260      15.0 
    ## 10 EWR     2013     1     1    10  41    28.0  59.6      260      13.8 
    ## # ℹ 348 more rows
    ## # ℹ 5 more variables: wind_gust <dbl>, precip <dbl>, pressure <dbl>,
    ## #   visib <dbl>, time_hour <dttm>

``` r
nrow(early_january_weather)
```

    ## [1] 358

``` r
ncol(early_january_weather)
```

    ## [1] 15

``` r
skimr::skim(early_january_weather)
```

|                                                  |                       |
|:-------------------------------------------------|:----------------------|
| Name                                             | early_january_weather |
| Number of rows                                   | 358                   |
| Number of columns                                | 15                    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                       |
| Column type frequency:                           |                       |
| character                                        | 1                     |
| numeric                                          | 13                    |
| POSIXct                                          | 1                     |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                       |
| Group variables                                  | None                  |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| origin        |         0 |             1 |   3 |   3 |     0 |        1 |          0 |

**Variable type: numeric**

| skim_variable | n_missing | complete_rate | mean | sd | p0 | p25 | p50 | p75 | p100 | hist |
|:---|---:|---:|---:|---:|---:|---:|---:|---:|---:|:---|
| year | 0 | 1.00 | 2013.00 | 0.00 | 2013.00 | 2013.00 | 2013.00 | 2013.00 | 2013.00 | ▁▁▇▁▁ |
| month | 0 | 1.00 | 1.00 | 0.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | ▁▁▇▁▁ |
| day | 0 | 1.00 | 8.04 | 4.31 | 1.00 | 4.00 | 8.00 | 12.00 | 15.00 | ▇▇▇▇▇ |
| hour | 0 | 1.00 | 11.53 | 6.92 | 0.00 | 6.00 | 11.50 | 17.75 | 23.00 | ▇▇▆▇▇ |
| temp | 0 | 1.00 | 39.58 | 7.06 | 24.08 | 33.98 | 39.02 | 44.96 | 57.92 | ▃▇▇▇▁ |
| dewp | 0 | 1.00 | 28.06 | 10.73 | 8.96 | 19.94 | 26.06 | 35.06 | 53.06 | ▃▇▆▂▃ |
| humid | 0 | 1.00 | 65.48 | 18.95 | 32.86 | 51.34 | 61.67 | 78.68 | 100.00 | ▃▇▆▂▅ |
| wind_dir | 5 | 0.99 | 208.19 | 115.58 | 0.00 | 140.00 | 240.00 | 290.00 | 360.00 | ▅▁▂▇▆ |
| wind_speed | 0 | 1.00 | 8.23 | 4.61 | 0.00 | 5.75 | 8.06 | 11.51 | 24.17 | ▅▇▆▂▁ |
| wind_gust | 308 | 0.14 | 22.53 | 3.63 | 16.11 | 19.56 | 21.86 | 25.32 | 31.07 | ▅▇▃▇▁ |
| precip | 0 | 1.00 | 0.00 | 0.01 | 0.00 | 0.00 | 0.00 | 0.00 | 0.19 | ▇▁▁▁▁ |
| pressure | 38 | 0.89 | 1022.52 | 5.57 | 1010.80 | 1018.30 | 1022.05 | 1027.23 | 1034.40 | ▃▇▇▇▃ |
| visib | 0 | 1.00 | 8.52 | 3.00 | 0.12 | 9.00 | 10.00 | 10.00 | 10.00 | ▁▁▁▁▇ |

**Variable type: POSIXct**

| skim_variable | n_missing | complete_rate | min | max | median | n_unique |
|:---|---:|---:|:---|:---|:---|---:|
| time_hour | 0 | 1 | 2013-01-01 01:00:00 | 2013-01-15 23:00:00 | 2013-01-08 12:30:00 | 358 |

``` r
write.csv(early_january_weather, "early_january_weather.csv", row.names = FALSE)
```

``` r
mean(early_january_weather$temp)
```

    ## [1] 39.58212

# Scatterplot

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
