---
title: "Lab 11"
date: "2021-04-15"
due_date: "2021-04-16"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 11
type: docs
editor_options: 
  chunk_output_type: console
---



## The questions on this lab are meant to be challenging. Do what you can, work in your groups, and try and solve the puzzles! You'll you many skills from throughout the semester. 


1. Create the following vector:

```r
nintendo <- c(Yoshi = 10L,
              Mario = 31L,
              Luigi = 72L,
              Peach = 11L,
              Toad  = 38L)
```

- Extract Yoshi and Peach from the above vector using:
    + Integer subsetting (with numbered indexes).
    + Negative integer subsetting (removal of unwanted indexes).
    + Logical subsetting (subsetting with TRUE/FALSE).
    + Name subsetting.



2. Create the following list:


```r
wedding <- list(venue = "chick-fil-a",
                guest = tidyr::tribble(~name,     ~meal, ~age,
                                ##--------/------/-----
                                "Yoshi",   "V",   29L,
                                "Wario",   "C",   27L,
                                "Bowser",  "V",   34L,
                                "Luigi",   "C",   36L,
                                "Toad",    "B",   34L), 
                bride = "Peach",
                groom = "Mario",
                date = lubridate::ymd("1999/04/01"))
```

2a. Wario can't actually make it. Remove his row from the data frame.



2b. Extract the venue and the date from `wedding`. Try to use three different techniques to do this.



2c. `"chick-fil-a"` should be capitalized. Capitalize the first `"c"` and last `"a"`.




3. Use a for loop to print out the following pattern:


```
##  1 
##  1 2 
##  1 2 3 
##  1 2 3 4 
##  1 2 3 4 5
```

4. Write a function that accepts a numeric vector. This function should loop through the vector and print out any number that is divisible by 5 and if a number is greater than 150, use "break" to stop the loop. (hint: `?break`). Use the following as input of your function: 




```r
div5(c(12,15,32,42,55,75,122,132,150,180,200))
```

```
## [1] 15
## [1] 55
## [1] 75
## [1] 150
```

5. Write a function to computer the factorial of a number. That is, the product of an integer and all the integers below it; e.g. `\(n! = n * (n-1) * (n-2) * .... * 2 * 1\)`
`\(facto(5) = 5 * 4 * 3 * 2 * 1 = 120\)`




```r
facto(5)
```

```
## [1] 120
```

```r
facto(7)
```

```
## [1] 5040
```

```r
facto(3)
```

```
## [1] 6
```



## Challenge
Combining Functions and loops with the Ice Cream Parlor
Adapted from [hackerrank](https://www.hackerrank.com/challenges/icecream-parlor/problem): 
Two friends like to pool their money and go to the ice cream parlor. They always
choose two distinct flavors and they spend all of their money. Given a list of
prices for the flavors of ice cream, select the two that will cost all of the
money they have.

Your icecreamParlor function should have the following parameter(s):  
- m: the amount of money they have to spend
- costs: a vector of the cost of each flavor of ice cream

and returns:
- a vector of length 2 which contains the the prices of the two flavors they buy, sorted ascending

Use **any** tools in this class to solve this problem, from nested loops to data wrangling. 




Example inputs and expected outputs you can test: 

```r
icecreamParlor(m = 4, costs = c(1, 4, 5, 3, 2))
```

```
## 1 3
```

```r
icecreamParlor(m = 6, costs = c(2, 4, 5, 3, 6))
```

```
## 2 4
```

```r
icecreamParlor(m = 8, costs = c(9, 4, 5, 3, 2))
```

```
## 3 5
```
