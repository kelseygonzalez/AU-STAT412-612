---
title: "Lab 3"
date: "2021-02-11"
due_date: "2021-02-12"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 3
type: docs
editor_options: 
  chunk_output_type: console
---



For this lab, complete part 1 and a at least one of the three following case studies. These are challenging but provide a real life example of what data wrangling looks like and I think each of you is capable of completing them! 

Note: Each of these steps is separate from each other, you should start with the raw `flights` data each time. 

# Part 1: Practice
1. Install the `nycflights13` package (using the console). It's likely you already have this from the textbook reading. Load the tidyverse package and nycflights13 package and the `flights` data that comes with the package.


2. Get a quick look at what your variables consist of and how many observations you have. Use `help(flights)` to get a qualitative understanding of what each of these variables represents.


3. Select all variables that include information about arrival or departure. Also keep the `year`, `month`, and `day`. Use as few characters as possible in your `select()` call. Double check your work - did you grab something you didn't actually want?


4. Find the flights that satisfy **all** of the following conditions:

    - Flew to Houston (IAH or HOU)
    - Were operated by United, American, or Delta (UA, AA, or DL)
    - Departed in summer (July, August, and September)
    - Arrived more than fifteen minutes late, but didn't leave late
      + Remember you can break lines after commas for easier readability
    - sort by the tail number in ascending order

    How many rows did you end up with? 

5. What is the minimum and maximum overall air_time? Your answer should be a dataframe with one row with two columns. 


5. What airline has the highest and lowest average departure delay? Try using functions so that you only get one row for your highest function and one row for your lowest function. 
    * hint: `slice_*()` is likely very useful here - explore the documentation! 
    * if you want to just grab the airline of the highest, `pull()` can also come in handy here. 


# Part 2: Flight Cancellations Case Study
You work for the hypothetical "New York City department of airplanes". They provide you with this dataset and you are asked to see if certain days of the month are more likely to have flight cancellations and perhaps why. 

1. Plot the proportion of canceled flights per day of the month.
    - You can tell a flight is canceled because the departure or arrival information is missing (hint: `is.na()`). 
    - If you create a "dummy" or "indicator" variable to indicate something is canceled, you can take the mean to calculate a proportion. (`mutate(is_cancelled = is.na(dep_delay) | is.na(arr_delay))`)
    - See the following plot to help guide you if you get stuck.
<img src="/assignment/03-lab_files/figure-html/unnamed-chunk-7-1.png" width="384" />
  
  
2. Does there seem to be a pattern?
3. Is the proportion of canceled flights related to the average daily delay?




# Part 3: Tail Numbers Case Study
You are offered a contract to do some analysis for the Regional Airline Association. They want you to tell them which tail numbers have changed airlines. Can you accept this contract?    

1. In two separate steps / functions, find the number or unique tail numbers and the combinations of airlines and tail numbers. Does the unique number or tail numbers match the unique combinations of airline and tailnumber? 


2. As shown above, there are more carrier-tail number combinations than unique tail numbers. There are two reasons for this: The presence of flights with no tail numbers and planes changing carriers. Find out which tail numbers belong to more than one carrier. Can you figure out how many tail numbers switched airlines but were _not_ flights with missing tail numbers? 



# Part 4: Delay Outliers Case Study
Your new position as data science intern for the Committee of Disgruntler Airline Passengers has been quite rewarding. The Director of the committee has focused their attention on how flight delays create a major headache for passengers and has asked you to do some investigation on how often flights are "_ridiculously_ delayed". 

1. There is a rule of thumb for outliers that is often used: Anything 1.5 interquartile ranges (IQR) above or below Q1/Q3 is an outlier. (i.e. `\(outlier < Q_1 - 1.5IQR\)`  or `\(outlier > Q_3 + 1.5IQR\)`) Can you use this rule to only select the flights that are outliers based on the dep_delay variable? How many flights are considered to be outliers according to this rule? 
    * remember that mutate adds a new column to all rows while summarize collapses the data into one row. 
    * to get the first and third quartile, use `quantile(x, 1/4)` and `quantile(x, 3/4)` respectively.

