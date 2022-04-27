Lab 10
================

For this lab we will carry out the paper helicopter experiment that you
helped design for Lab 9 and HW 4. We will use a randomized complete
block design, with subsamples.

Using the following guide
(<https://www.wikihow.com/Create-a-Paper-Helicopter>) each student (and
block) will make a total of 4 helicopters.

-   `wing_length`: 8 cm and 12 cm
-   `wing_width`: 3 cm and 6 cm

Run the following code and update `set.seed()` with your birthday
`set.seed(MMDD)`to determine the order that you make and drop the
helicopters.

``` r
set.seed(1015)
tibble(EU = 1:4,
       trt = sample(paste('length ', rep(c(8, 12),2), '; width ', rep(c(3, 6), each = 2), sep = '')))
```

    ## # A tibble: 4 × 2
    ##      EU trt               
    ##   <int> <chr>             
    ## 1     1 length 12; width 6
    ## 2     2 length 8; width 6 
    ## 3     3 length 8; width 3 
    ## 4     4 length 12; width 3

There is no official protocol for body length, but be consistent across
your 4 helicopters.

To understand the observational error (differences in drop time for the
same helicopter), each helicopter will be dropped and timed three times.

Please submit the following a CSV file with the following structure,
where time contains the time before the helicopter touches the ground.

``` r
tibble(EU = rep(1:4, each = 3),
       trt = rep(paste('length ', rep(c(8, 12),2), '; width ', rep(c(3, 6), each = 2), sep = ''), each = 3),
       OU = rep(1:3, 4),
       time = 4)
```

    ## # A tibble: 12 × 4
    ##       EU trt                   OU  time
    ##    <int> <chr>              <int> <dbl>
    ##  1     1 length 8; width 3      1     4
    ##  2     1 length 8; width 3      2     4
    ##  3     1 length 8; width 3      3     4
    ##  4     2 length 12; width 3     1     4
    ##  5     2 length 12; width 3     2     4
    ##  6     2 length 12; width 3     3     4
    ##  7     3 length 8; width 6      1     4
    ##  8     3 length 8; width 6      2     4
    ##  9     3 length 8; width 6      3     4
    ## 10     4 length 12; width 6     1     4
    ## 11     4 length 12; width 6     2     4
    ## 12     4 length 12; width 6     3     4

Hint, you can use `write_csv()` in R to pass an R data frame to a CSV
file.
