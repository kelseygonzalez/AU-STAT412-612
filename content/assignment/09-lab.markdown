---
title: "Lab 9"
date: "2021-04-01"
due_date: "2021-04-02"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 8
type: docs
editor_options: 
  chunk_output_type: console
---

# Learning Outcomes
- Use `forcats` functions to manage factors in R
- Use `lubridate` functions in R in conjunction with functions from `dplyr` and `tidyr`.

# Factors

1. Load the `gss_cat` data from the `forcats` package. 


2. Find how many observations fell into each factor level of `rincome`. Don't overthink this one - it's one function we've been using for over a month!


3. Plot a barplot of the distribution of `rincome`, ordering levels from by frequency


4. You think "Not applicable", "Don't Know", "No answer", and "Refused" aren't very useful for your plot. Use `fct_other()` to collapse these into one factor level and *plot again*. Note: `fct_other()` is new! Read the documentation. 


5. Reorder the levels of the relig variable by the mean number of tv hours watched. Show the new factor order when complete. Plot with a boxplot. 


# dates

1. Many people have created a "Coronavirus Birthday", the first date they went into lockdown, quarantine, or began extreme social distancing. This is usually in March 2020. Many seconds have passed since this time (i.e., calculate the duration in seconds)? If you can't remember, use March 15, 2020. 


2. Use `seconds_to_period()` to go from your duration (q1) to the period since your "Coronavirus Birthday". 


3. For the rest of this exercise, we will use the data from [<i class="fas fa-file-csv"></i> `capital_trips_2016.csv`](/data/capital_trips_2016.csv). Read these data into R from the data directory and review the variables with `glimpse()`. These data are from a bikesharing program.



4. Rename variables to conform to "best practices" for variable names i.e., no spaces in the names. Feel free to  experiment with the handy `janitor::clean_names()` function here if you'd like. 




5. Convert the start date and end date variables to be date-times.



6. Use the start date and end date variables to calculate the duration of each trip. 




7. How much time elapsed between the start of the first trip and the end of the the last trip.





