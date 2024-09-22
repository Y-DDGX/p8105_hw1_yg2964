Homework 1
================

Name: Yuchen Gu Uni:yg2964

# Problem 1

## Section 1 - Data import and Description

``` r
data("penguins", package = "palmerpenguins")
```

The penguins dataset contains information about three penguins species :
Adelie, Chinstrap, and Gentoo. It has 344 observations and 8 variables.

This dataset includes details about each penguin such as its species,
the island where it lives, and various body measurements. These
measurements include bill length and depth, flipper length, and body
mass. It also records the sex of each penguin and the year of
observation. From this data, we can see that the average flipper length
of the penguins is 200.92 mm, and their average body mass is 4201.75 g.

It’s important to note that the dataset isn’t perfect. There are some
missing values: 2 for body mass and 11 for sex.

Scientists can use this data to study differences between penguin
species, how penguins might vary across islands, and differences between
male and female penguins. This helps in understanding penguin biology
and their adaptation to the Antarctic environment.

## Section 2 - Scatterplot Creation

![](HW1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

This scatterplot effectively illustrates the relationship between bill
length and flipper length across three penguin species. Distinct
clusters are visible, with Gentoo penguins (blue) showing longer
flippers and bills, Adelie penguins (red) having shorter measurements in
both dimensions, and Chinstrap penguins (green) occupying a middle
ground. A positive correlation between bill length and flipper length is
apparent within each species.

# Problem 2

## Section 1 - Creating the Data Frame

``` r
set.seed(17)

problem2_df = tibble(
  random_sample = rnorm(10),
  log_vector = random_sample > 0,
  char_vector = letters[1:10],
  factor_vector = factor(rep(c("Low", "Medium", "High"), length.out = 10))
)

problem2_df
```

    ## # A tibble: 10 × 4
    ##    random_sample log_vector char_vector factor_vector
    ##            <dbl> <lgl>      <chr>       <fct>        
    ##  1       -1.02   FALSE      a           Low          
    ##  2       -0.0796 FALSE      b           Medium       
    ##  3       -0.233  FALSE      c           High         
    ##  4       -0.817  FALSE      d           Low          
    ##  5        0.772  TRUE       e           Medium       
    ##  6       -0.166  FALSE      f           High         
    ##  7        0.973  TRUE       g           Low          
    ##  8        1.72   TRUE       h           Medium       
    ##  9        0.255  TRUE       i           High         
    ## 10        0.367  TRUE       j           Low

## Section 2 - Calculating Means

``` r
mean(pull(problem2_df, random_sample), na.rm = TRUE)
mean(pull(problem2_df, log_vector), na.rm = TRUE)
mean(pull(problem2_df, char_vector), na.rm = TRUE)
mean(pull(problem2_df, factor_vector), na.rm = TRUE)
```

The mean of the random sample is 0.1772805, and the mean of the logical
vector is 0.5.

As expected, attempting to calculate the mean of the character vector
results in NA with a warning, because ‘a’ and other letters cannot be
averaged. Similarly, the mean of the factor vector also returns NA, as
High, Low, and Medium cannot be directly averaged without first
converting to numeric values.

## Section 3 - Conversion with as.numeric

``` r
numeric_log <- as.numeric(pull(problem2_df, log_vector))
numeric_char <- as.numeric(pull(problem2_df, char_vector))
numeric_factor <- as.numeric(pull(problem2_df, factor_vector))
```

Converting different data types to numeric yields varied results:

1.  Logical to Numeric: Successful. TRUE becomes 1, FALSE becomes 0.
2.  Character to Numeric: Results in NAs. Letters can’t be directly
    converted to numbers.
3.  Factor to Numeric: Converts to integer levels. “Low”, “Medium”,
    “High” might become 1, 2, 3.

These conversions explain our earlier mean calculation results: -
Logical vector mean worked (converted to 0s and 1s). - Character vector
mean failed (can’t convert to numbers). - Factor vector mean failed
initially but can be calculated after conversion to numeric.

Recalculate the mean:

``` r
mean_numeric_log <- mean(numeric_log, na.rm = TRUE)
mean_numeric_char <- mean(numeric_char, na.rm = TRUE)
mean_numeric_factor <- mean(numeric_factor, na.rm = TRUE)
```

After converting to numeric and recalculating means:

1.  Logical vector: Mean is 0.5, representing the proportion of TRUE
    values.
2.  Character vector: Mean is NaN. It’s NA because characters couldn’t
    be converted to numbers.
3.  Factor vector: Mean is 2, reflecting the average of the numeric
    levels assigned to factors.
