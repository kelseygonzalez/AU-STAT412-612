---
title: "Lab 2"
date: "2021-02-04"
due_date: "2021-02-05"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 2
type: docs
toc: true
editor_options: 
  chunk_output_type: console
---



# 1. Gapminder
![](https://storage.googleapis.com/kaggle-datasets-images/373567/726490/b870208e6f91c6a6c940f8a4df111c87/dataset-cover.png?t=2019-10-22-19-47-34)

The goal of the gapminder dataset is to explore the relationship between GDP, population, and life expectancy.

1.  Use `data()` to load the `gapminder` dataset from the `gapminder` package (hint: you'll need to install this!). Also load the `tidyverse` package. 

2. Create a barplot (hint: `geom_bar()`) for total counts for the different continents. Why do you think there are so many countries in each continent? Do some digging through the data's structure untily you're able to explain why, fore example, there are 396 counties in Asia in this dataset.

3.  Create a scatterplot (hint: `geom_point()`) with year (`year`) on the x-axis, life expectancy (`lifeExp`) on the y-axis, and with the points colored by continent (`continent`). Make this a longitudinal / time-series plot by adding geom_line (this is a new one for us!). Hint: To fix the incorrect mapping, how will you tell ggplot that the lines should follow the country column?

4.  Create a density plot with life expectancy (`lifeExp`) on the x-axis. Do not include anything on the y-axis. What ways can we disaggregate this density plot by adding in continent (I can immediately think of 3 we covered in class)? What do you learn about the continents?

    -   Add a title, axis labels, and a new theme to your preferred plot.
    -   Try to customize the color or fill property with a special scale - either create your own (`scale_fill_manual(values = c())`) or use a predefined scale from `ggplot2` or `ggthemes`.

5.  Finally, create a scatter plot that explores the relationship between x, `gdpPercap` and y, `lifeExp`.

    -   Map color to continent and add a OLS lm smooth line for each continent.
    -   Because GDP is so skewed, transform the x scale to a log10 (hint: `scale_x_log10()`)
    -   The log scale has ugly labels. Try using `scale_x_log10(labels=scales::comma)` if you download the scales package.
    -   Try moving the legend for continents into the plot frame, e.g., by adding `+ theme(legend.position = c(0.8, 0.2))`. What do those numbers seem to do?
    -   Try changing the theme for this plot to one that you like from either base `ggplot2` or from the `ggthemes` package. Why do you like this theme?
    -   Try making a "bubble" plot by mapping the size of each point to the point's population (`pop`)


**As announced in class, the Diamonds part is optional for your turned in version of the lab.**



# 2. Diamonds
![](https://datasciencereview.com/wp-content/uploads/2018/08/Diamond-Carat-Relationship.png)
The goal of the diamonds dataset is to see which characteristics are most influential on price.

1.  Use `data()` to load the `diamonds` dataset from ggplot2.

2.  Perform an exploratory data analysis and develop some conjectures on what variables impact price.

    -   Make plots of price vs each of the four other (`carat`, `cut`, `color`, `clarity`) variables. Use the type of plot appropriate to each specific types of variables. For instance, is the secondary variable quantitative or categorical? 

    -   Consider if transforming the variables or scales (like a log transformation) might be relevant to one of your axes.

    -   Can some surprising associations be explained by other variables?

        -   For example, can the decrease in price as the cut worsens be explained by the carat of the diamond?
