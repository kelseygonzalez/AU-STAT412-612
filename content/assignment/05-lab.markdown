---
title: "Lab 5"
date: "2021-02-25"
due_date: "2021-02-26"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 5
type: docs
editor_options: 
  chunk_output_type: console
---



# 1. Gapminder
![](https://storage.googleapis.com/kaggle-datasets-images/373567/726490/b870208e6f91c6a6c940f8a4df111c87/dataset-cover.png?t=2019-10-22-19-47-34)

The goal of the gapminder dataset is to explore the relationship between GDP, population, and life expectancy.


1. Load the `tidyverse` package and the `gapminder` dataset from the `gapminder` package.

2. What are the mean life expectancies and populations seen by year for each
continent?



  
3. Using `across()`, can you get the min, mean, median, and max life expectancy for each country? 



4. Building off of your last answer, can you use `rowwise()` and `mutate()` to
calculate the range for each country, subtracting lifeExp_min from lifeExp_max?
Arrange descending by your new lifeExp_range variable. 
    + Yes, there is a `range()` function you could have used in your `across()`
    function call. While you can _validate_ your max-min subtraction with that, I'd 
    like you to practice `rowwise()` here!


5. How many countries are there on each continent, excluding duplicates?




# 2. Diamonds
![](https://datasciencereview.com/wp-content/uploads/2018/08/Diamond-Carat-Relationship.png)
The goal of the diamonds dataset is to see which characteristics are most influential on price.

1.  Use `data()` to load the `diamonds` dataset from ggplot2.


2. According to the diamond documentation, the variable `depth` is calculated 
using the formula `\(total depth percentage = 100 * z / mean(x, y)\)`. Implement this formula using `rowwise()` and `mutate()`. Name your new variable `depth_check`. 


3. Using `case_when()`, create an indicator variable `perfect` of all diamonds that meet the following conditions:
    + cut is premium or ideal & color is D or E & carat is bigger than 1 & clarity is VVS1 or IF. 
create a plot with this new variable of carat (x) by price (y), colored by "perfect". Here's some code to get your started...
```
diamonds %>% 
  mutate(perfect = case_when((cut conditions) & 
                               (color conditions) & 
                               (carat conditions) &
                               (clarity conditions) ~ "Perfect",",
                             TRUE ~ "Not Perfect")) %>% 
  ggplot()
```





