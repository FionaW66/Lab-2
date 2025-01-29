Lab 02 - Plastic waste
================
Fiona Wang
Jan-28-2025

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read.csv("data/plastic-waste.csv")
```

## Exercises

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) + 
  geom_histogram(binwidth = 0.2)
```

![](lab-02_files/figure-gfm/initial%20ggplot-1.png)<!-- -->

There is one country that stands out, let’s filter to find this country!

``` r
plastic_waste %>%
  filter(plastic_waste_per_cap > 3.5)
```

    ##   code              entity     continent year gdp_per_cap plastic_waste_per_cap
    ## 1  TTO Trinidad and Tobago North America 2010    31260.91                   3.6
    ##   mismanaged_plastic_waste_per_cap mismanaged_plastic_waste coastal_pop
    ## 1                             0.19                    94066     1358433
    ##   total_pop
    ## 1   1341465

It is Trinidad and Tobago from North America. I didn’t expect this
result, mainly because it is a country that I am not familiar with. It
seems like they have high consumption of single-use plastics and limited
recycling infrastructure.

### Exercise 1

It seems like there weren’t a lot of countries reported on Oceania and
South America, so they seem to have less plastic waste. North America
has the outlier (Trinidad and Tobago). Most countries plastic waste is
between 0 to 0.5.The tallest bars among these graphs are 0.0-0.2 and
0.2-0.4.

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap, color = continent)) + 
  geom_histogram(binwidth = 0.2) + 
  facet_wrap(~continent, ncol = 3)
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

Another way of visualizing is using density plots.

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) + 
  geom_density()
```

![](lab-02_files/figure-gfm/density%20plots-1.png)<!-- -->

Compare distributions across continent by coloring density curves by
continent.

``` r
ggplot(data = plastic_waste, mapping = aes(x=plastic_waste_per_cap, 
       color = continent)) +
  geom_density()
```

![](lab-02_files/figure-gfm/compare%20density-1.png)<!-- -->

Fill the curves of the density graph and adjust the transparency.

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, color = continent,
                     fill = continent)) + 
  geom_density(alpha = 0.3)
```

![](lab-02_files/figure-gfm/fill%20density-1.png)<!-- -->

### Exercise 2

``` r
# insert code here
```

### Exercise 3

Remove this text, and add your answer for Exercise 3 here.

``` r
# insert code here
```

### Exercise 4

Remove this text, and add your answer for Exercise 4 here.

``` r
# insert code here
```

``` r
# insert code here
```

``` r
# insert code here
```

``` r
# insert code here
```

### Exercise 5

Remove this text, and add your answer for Exercise 5 here.

``` r
# insert code here
```
