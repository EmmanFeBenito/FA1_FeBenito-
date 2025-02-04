SEC1-FA1 GROUP 15-FE BENITO,E
================
Emmanuel Fe Benito
2025-02-02

## 1.

### What can you say about these data?

The data is a lot and quite varied.

``` r
data <- read.csv("C:/Users/Emmanuel/Documents/results.txt")
```

### Pearson Skewness Function

``` r
pearson_skewness <- function(column) {
  mean_val <- mean(column, na.rm = TRUE)  
  median_val <- median(column, na.rm = TRUE) 
  std_dev <- sd(column, na.rm = TRUE)
  skewness <- 3 * (mean_val - median_val) / std_dev
  return(skewness)
}

skewness_results <- sapply(data[, -1], pearson_skewness)
print(skewness_results)
```

    ##      arch1      prog1      arch2      prog2 
    ## -0.6069042 -0.6432290  0.5421286 -0.3562908

### Exact Skewness Calculation

``` r
library(e1071)
exact_skewness <- sapply(data[, -1], skewness, na.rm = TRUE)
print(exact_skewness)
```

    ##      arch1      prog1      arch2      prog2 
    ## -0.5063276 -0.3291610  0.4423272 -0.2977574

### Is it a reasonable approximation?

It is somewhat reasonable. The difference is fairly negligible, though
it is still inaccurate. If looking for trends, it’s fairly reasonable,
but if accuracy is the concern, then it’s best not to rely on it.

## 2.

``` r
Females <- c(57, 59, 78, 79, 60, 65, 68, 71, 75, 48, 51, 55, 56, 41, 43,
             44, 75, 78, 80, 81, 83, 83, 85)
Males <- c(48, 49, 49, 30, 30, 31, 32, 35, 37, 41, 86, 42, 51, 53, 56,
           42, 44, 50, 51, 65, 67, 51, 56, 58, 64, 64, 75)
```

### Stem-and-Leaf Display

``` r
stem(Females)
```

    ## 
    ##   The decimal point is 1 digit(s) to the right of the |
    ## 
    ##   4 | 1348
    ##   5 | 15679
    ##   6 | 058
    ##   7 | 155889
    ##   8 | 01335

``` r
stem(Males)
```

    ## 
    ##   The decimal point is 1 digit(s) to the right of the |
    ## 
    ##   3 | 001257
    ##   4 | 1224899
    ##   5 | 01113668
    ##   6 | 4457
    ##   7 | 5
    ##   8 | 6

### Stem-and-Leaf Display Discussion

This presentation showcases the raw individual values, allowing for more
precise evaluation compared to a histogram.

### Box-Plots

``` r
boxplot(Females, main="Females Box-Plot", ylab="Scores")
```

![](SEC1-FA1-GROUP-15-FE-BENITO,E_files/figure-gfm/box-plots-1.png)<!-- -->

``` r
boxplot(Males, main="Males Box-Plot", ylab="Scores")
```

![](SEC1-FA1-GROUP-15-FE-BENITO,E_files/figure-gfm/box-plots-2.png)<!-- -->

### Analysis of Box-Plots

- The box plot shows that the scores are significantly higher on average
  for the females compared to the males.
- The box plot for females is also bigger, showing more variation in
  scores compared to the smaller and more compact male scores.
- There’s also an outlier in the male’s box plot way up in the 80s, but
  none in the female’s box plot.
