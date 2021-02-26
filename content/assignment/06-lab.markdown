---
title: "Lab 6"
date: "2021-03-04"
due_date: "2021-03-05"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 6
type: docs
editor_options: 
  chunk_output_type: console
---

## Import untidy Lord of the Rings data

Get them into your current project in a `data` subdirectory with your favorite method:


# Tidy Data
Data comes in many formats but R prefers just one: _tidy data_.

A data set is tidy if and only if:

1. Every variable is in its own column
2. Every observation is in its own row
3. Every value is in its own cell (which follows from the above)

# Lab Questions
1. Download the lotr_untidy.csv data and save to your data folder.

- [<i class="fas fa-file-csv"></i> `lotr_untidy1.csv`]("/data/lotr_untidy1.csv")  
- [<i class="fas fa-file-csv"></i> `lotr_untidy2.csv`]("/data/lotr_untidy2.csv")

About the data:

Publication: J.R.R. Tolkien. The Lord of the Rings. Ballantine Books, New York. Copyright 1954-1974. Volume I. The Fellowship of the Ring. Volume II. The Two Towers. Volume III. The Return of the King.

Downloaded from: [jennybc on github](https://github.com/jennybc/lotr-tidy/)

Variables:   
    - Film: The Lord of The Rings Film  
    - Race: The Race of the Characters     
    - Female: word spoken by females in LOTR  
    - Male: word spoken by males in LOTR  
    - FOTR_ROTK_TTT: Words spoken in each book of Fellowship of the Ring, The Return of the King, and The Two Towers.

2. Load both of the files. Explain what makes each data frame untidy. 

3. Using the skills learned in class, make lotr_untidy1 _tidy._ 

4. What’s the total number of words spoken by male hobbits?

5. Does a certain Race dominate (meaning, speak the most words) a movie? Does the dominant Race differ across the movies? Is there a way you can visualize this? 

6. Using the skills learned in class, make lotr_untidy2 _tidy._ 
