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

## Section 2 Scatterplot Creation

![](HW1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

This scatterplot effectively illustrates the relationship between bill
length and flipper length across three penguin species. Distinct
clusters are visible, with Gentoo penguins (blue) showing longer
flippers and bills, Adelie penguins (red) having shorter measurements in
both dimensions, and Chinstrap penguins (green) occupying a middle
ground. A positive correlation between bill length and flipper length is
apparent within each species.
