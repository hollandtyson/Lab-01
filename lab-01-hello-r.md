Lab 01 - Hello R
================
Holland Tyson
1/29/2023

## Load packages and data

``` r
library(tidyverse) 
library(datasauRus)
```

## Exercises

### Exercise 1

1846 rows and 3 variables which are dataset, x, and y.

### Exercise 2

The answers for this exercise are given for you below. But you should
clean up some of the narrative so that it only includes what you want to
turn in.

First let’s plot the data in the dino dataset:

``` r
dino_data <- datasaurus_dozen %>%
  filter(dataset == "dino")

ggplot(data = dino_data, mapping = aes(x = x, y = y)) +
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-dino-1.png)<!-- -->

And next calculate the correlation between `x` and `y` in this dataset:
-0.0645

``` r
dino_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0645

### Exercise 3

Add code and narrative as needed. Note that the R chunks are labeled
with `plot-star` and `cor-star` to provide spaces to place the code for
plotting and calculating the correlation coefficient.

``` r
dino_data <- datasaurus_dozen %>%
  filter(dataset == "star")

ggplot(data = dino_data, mapping = aes(x =x, y = y)) +
 geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-star-1.png)<!-- -->

Now calculate the coreelation between x and y

``` r
 dino_data %>%
 summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0630

### Exercise 4

Add code and narrative as needed. Note that two R chunks are given but
they are not labeled. Use the convention from above to name them
appropriately.

``` r
dino_data <- datasaurus_dozen %>%
 filter(dataset == "circle")
 ggplot(data = dino_data, mapping = aes(x = x, y = y)) +
 geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-circle-1.png)<!-- -->

``` r
 dino_data %>%
 summarize(r = cor(x, y))
```

    ## # A tibble: 1 × 1
    ##         r
    ##     <dbl>
    ## 1 -0.0683

### Exercise 5

Add code and narrative as needed.

To add R chunks either type out the backticks, curly braces, and the
letter `r` or use the Insert chunk button above, green C+.

``` r
 ggplot(datasaurus_dozen, aes(x =x, y = y, color = dataset))+
 geom_point()+
 facet_wrap(~ dataset, ncol = 3) +
 theme(legend.position = "none")
```

![](lab-01-hello-r_files/figure-gfm/plot-all-1.png)<!-- -->

``` r
datasaurus_dozen %>%
 group_by(dataset) %>%
 summarize(r = cor(x, y)) %>%
 print(13)
```

    ## # A tibble:
    ## #   13 × 2
    ##    dataset   
    ##    <chr>     
    ##  1 away      
    ##  2 bullseye  
    ##  3 circle    
    ##  4 dino      
    ##  5 dots      
    ##  6 h_lines   
    ##  7 high_lines
    ##  8 slant_down
    ##  9 slant_up  
    ## 10 star      
    ## 11 v_lines   
    ## 12 wide_lines
    ## 13 x_shape   
    ## # … with 1
    ## #   more
    ## #   variable:
    ## #   r <dbl>
