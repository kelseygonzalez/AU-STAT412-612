---
title: "Lab 10"
date: "2021-04-08"
due_date: "2021-04-09"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 10
type: docs
editor_options: 
  chunk_output_type: console
---


1. Create a function that takes a variable as input and outputs a standardized version of that column.
    - A standardized / normalized variable takes the datapoint (each row / observation) minus the mean of the variable divided by the standard deviation of the variable. In mathematical notation,  `\(Z = \frac{x - \mu}{ \sigma}\)`
    - Build in tests and stops that makes sure the variable (1) has more than one observation (`length()`), and (2) is numeric.
    - Build in a return statement

 
 
2. Load the gapminder data and run your function on `gapminder$lifeExp` and `gapminder$country`. Show the first six values of the output. 



