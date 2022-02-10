Lab4
================

For this lab we will be starting to think about analyzing our airplane
data. Clean the `Airplane` dataset and recreate a figure similar to lab
2.

``` r
airplane <- read_csv("Airplane.csv")
```

``` r
airplane <- airplane %>% 
  mutate(id = 1:n(), feet_dec = -99) %>% 
  pivot_longer(cols = c(Dart,Glider))
```
