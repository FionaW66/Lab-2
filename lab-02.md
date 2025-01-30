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

### Exercise 1 Histogram

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
  geom_density(alpha = 0.7)
```

![](lab-02_files/figure-gfm/fill%20density-1.png)<!-- -->

### Exercise 2 Recreate density plot

To compare between mapping and setting/geom, I am trying out the
following two ways. First, let’s use geom_density to define color and
fill, and we use mapping to define alpha. The second way is to put color
and fill in mapping while defining alpha in the setting/geom.

``` r
#The first way
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, alpha = 0.1)) + 
  geom_density(color = "pink", fill = "blue")
```

![](lab-02_files/figure-gfm/plastic-waste-density%20lower%20alpha-1.png)<!-- -->

``` r
#The second way
ggplot(data = plastic_waste, 
       mapping = aes(x = plastic_waste_per_cap, 
                     color = continent, fill = continent)) +
  geom_density(alpha = 0.1)
```

![](lab-02_files/figure-gfm/plastic-waste-density%20lower%20alpha-2.png)<!-- -->

2.2 answer: As we can see, if we define color and fill in geom_density,
we cannot distinguish between each continent, as this will be a setting
for all of the continents. If we put color and fill in mapping, we can
ask R to map each continent using different colors. For alpha, when I
put it in the mapping, no transparency took place. Also, we want the
same transparency to be applied to each of the continent. This is why we
just define alpha in the setting, so it can be applied globally.

Another way to visualize is using box plots.

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = continent, y = plastic_waste_per_cap)) +
  geom_boxplot()
```

![](lab-02_files/figure-gfm/box%20plot-1.png)<!-- -->

### Exercise 3 Violin

Both boxplot and violin plot give us outliers. The boxplot gives us the
median and quartiles that a violin plot doesn’t. A violin plot can give
you the distribution of each continent which the boxplot doesn’t.

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = continent, y = plastic_waste_per_cap)) +
  geom_violin()
```

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

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
