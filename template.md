Simple document
================

## import data, FAS\_litters.csv

``` r
litters_data = read_csv(file = "data_import_examples/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_data
```

    ## # A tibble: 49 × 8
    ##    Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##    <chr> <chr>                  <dbl>         <dbl>         <dbl>
    ##  1 Con7  #85                     19.7          34.7            20
    ##  2 Con7  #1/2/95/2               27            42              19
    ##  3 Con7  #5/5/3/83/3-3           26            41.4            19
    ##  4 Con7  #5/4/2/95/2             28.5          44.1            19
    ##  5 Con7  #4/2/95/3-3             NA            NA              20
    ##  6 Con7  #2/2/95/3-2             NA            NA              20
    ##  7 Con7  #1/5/3/83/3-3/2         NA            NA              20
    ##  8 Con8  #3/83/3-3               NA            NA              20
    ##  9 Con8  #2/95/3                 NA            NA              20
    ## 10 Con8  #3/5/2/2/95             28.5          NA              20
    ## # … with 39 more rows, and 3 more variables: Pups born alive <dbl>,
    ## #   Pups dead @ birth <dbl>, Pups survive <dbl>

## cleaning variable names imported

``` r
names(litters_data)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

``` r
## [1] "Group"             "Litter Number"     "GD0 weight"       
## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
## [7] "Pups dead @ birth" "Pups survive"


# cleans variables and turns  them into lower snake case
# useful for tidying  variable names of imported csv
litters_data = janitor::clean_names(litters_data) 

names(litters_data)
```

    ## [1] "group"           "litter_number"   "gd0_weight"      "gd18_weight"    
    ## [5] "gd_of_birth"     "pups_born_alive" "pups_dead_birth" "pups_survive"

## viewing data

``` r
# litters_data
# tail(litters_data, 5) # last 5
# head(litters_data, 5) # fisrt 5
# view(litters_data) # opens separate tab with data table, make sure commented when knitting
# str(litters_data) # puts all columns into lists
skimr::skim(litters_data) # creates data summary and shows simple hist for each var
```

|                                                  |               |
|:-------------------------------------------------|:--------------|
| Name                                             | litters\_data |
| Number of rows                                   | 49            |
| Number of columns                                | 8             |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |               |
| Column type frequency:                           |               |
| character                                        | 2             |
| numeric                                          | 6             |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |               |
| Group variables                                  | None          |

Data summary

**Variable type: character**

| skim\_variable | n\_missing | complete\_rate | min | max | empty | n\_unique | whitespace |
|:---------------|-----------:|---------------:|----:|----:|------:|----------:|-----------:|
| group          |          0 |              1 |   4 |   4 |     0 |         6 |          0 |
| litter\_number |          0 |              1 |   3 |  15 |     0 |        49 |          0 |

**Variable type: numeric**

| skim\_variable    | n\_missing | complete\_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:------------------|-----------:|---------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0\_weight       |         15 |           0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18\_weight      |         17 |           0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd\_of\_birth     |          0 |           1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups\_born\_alive |          0 |           1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups\_dead\_birth |          0 |           1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups\_survive     |          0 |           1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

## arguments in ‘read\_csv’

``` r
litters_df = read_csv("data_import_examples/FAS_litters.csv",
                      skip = 5,
                      col_names = FALSE,
                      na = "Low8") #  replace missing data w na
```

    ## Rows: 45 Columns: 8

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df
```

    ## # A tibble: 45 × 8
    ##    X1    X2              X3    X4       X5    X6    X7    X8
    ##    <chr> <chr>           <chr> <chr> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con7  #4/2/95/3-3     NA    NA       20     6     0     6
    ##  2 Con7  #2/2/95/3-2     NA    NA       20     6     0     4
    ##  3 Con7  #1/5/3/83/3-3/2 NA    NA       20     9     0     9
    ##  4 Con8  #3/83/3-3       NA    NA       20     9     1     8
    ##  5 Con8  #2/95/3         NA    NA       20     8     0     8
    ##  6 Con8  #3/5/2/2/95     28.5  NA       20     8     0     8
    ##  7 Con8  #5/4/3/83/3     28    NA       19     9     0     8
    ##  8 Con8  #1/6/2/2/95-2   NA    NA       20     7     0     6
    ##  9 Con8  #3/5/3/83/3-3-2 NA    NA       20     8     0     8
    ## 10 Con8  #2/2/95/2       NA    NA       19     5     0     4
    ## # … with 35 more rows

## Parsing columns

``` r
litters_data = read_csv(file = "data_import_examples//FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  ) # specify column types
)

# short hand for specifying col types
# litters_data = read_csv(file = "./data/FAS_litters.csv",
#   col_types = "ccddiiii"
# )

tail(litters_data)
```

    ## # A tibble: 6 × 8
    ##   Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##   <chr> <chr>                  <dbl>         <dbl>         <int>
    ## 1 Low8  #79                     25.4          43.8            19
    ## 2 Low8  #100                    20            39.2            20
    ## 3 Low8  #4/84                   21.8          35.2            20
    ## 4 Low8  #108                    25.6          47.5            20
    ## 5 Low8  #99                     23.5          39              20
    ## 6 Low8  #110                    25.5          42.7            20
    ## # … with 3 more variables: Pups born alive <int>, Pups dead @ birth <int>,
    ## #   Pups survive <int>

## other file formats

## read\_csv (tibbles) better than read.csv

``` r
library(readxl)

mlb11_data = read_excel("data_import_examples/mlb11.xlsx", n_max = 20)
head(mlb11_data, 20)
```

    ## # A tibble: 20 × 12
    ##    team        runs at_bats  hits homeruns bat_avg strikeouts stolen_bases  wins
    ##    <chr>      <dbl>   <dbl> <dbl>    <dbl>   <dbl>      <dbl>        <dbl> <dbl>
    ##  1 Texas Ran…   855    5659  1599      210   0.283        930          143    96
    ##  2 Boston Re…   875    5710  1600      203   0.28        1108          102    90
    ##  3 Detroit T…   787    5563  1540      169   0.277       1143           49    95
    ##  4 Kansas Ci…   730    5672  1560      129   0.275       1006          153    71
    ##  5 St. Louis…   762    5532  1513      162   0.273        978           57    90
    ##  6 New York …   718    5600  1477      108   0.264       1085          130    77
    ##  7 New York …   867    5518  1452      222   0.263       1138          147    97
    ##  8 Milwaukee…   721    5447  1422      185   0.261       1083           94    96
    ##  9 Colorado …   735    5544  1429      163   0.258       1201          118    73
    ## 10 Houston A…   615    5598  1442       95   0.258       1164          118    56
    ## 11 Baltimore…   708    5585  1434      191   0.257       1120           81    69
    ## 12 Los Angel…   644    5436  1395      117   0.257       1087          126    82
    ## 13 Chicago C…   654    5549  1423      148   0.256       1202           69    71
    ## 14 Cincinnat…   735    5612  1438      183   0.256       1250           97    79
    ## 15 Los Angel…   667    5513  1394      155   0.253       1086          135    86
    ## 16 Philadelp…   713    5579  1409      153   0.253       1024           96   102
    ## 17 Chicago W…   654    5502  1387      154   0.252        989           81    79
    ## 18 Cleveland…   704    5509  1380      154   0.25        1269           89    80
    ## 19 Arizona D…   731    5421  1357      172   0.25        1249          133    94
    ## 20 Toronto B…   743    5559  1384      186   0.249       1184          131    81
    ## # … with 3 more variables: new_onbase <dbl>, new_slug <dbl>, new_obs <dbl>

## only load in certain part of Excel file

``` r
fellow_df = read_excel("data_import_examples/LotR_Words.xlsx", range = "B3:D6")
fellow_df
```

    ## # A tibble: 3 × 3
    ##   Race   Female  Male
    ##   <chr>   <dbl> <dbl>
    ## 1 Elf      1229   971
    ## 2 Hobbit     14  3644
    ## 3 Man         0  1995

``` r
library(haven)

pulse_data = read_sas("data_import_examples/public_pulse_data.sas7bdat")
head(pulse_data, 5)
```
