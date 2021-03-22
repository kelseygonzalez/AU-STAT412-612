---
title: "Lab 8"
date: "2021-03-25"
due_date: "2021-03-26"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 8
type: docs
editor_options: 
  chunk_output_type: console
---




Load the tidyverse and the `stringr::words` and `stringr::fruit` vectors. You won't be able to use the `data()` function, you'll have to assign `stringr::words` to a new object.



## find matches 
reminder: using `str_view()` will help you test and build your regular expressions. 

1. Find words (from the `words` vector) that start with a vowel using `str_subset()`. You should have 175 words. 


2. Find words (from the `words` vector) that end with at least 2 consecutive consonants using `str_subset()`.  (Hint: thinking about matching "not"-vowels.). You should have 353 words. 


3. Find words (from the `words` vector) that end with either "ing", "ize" or "ise" using `str_subset()`. You should have 20 words. 


## replace 

4. You decide berries cannot be singular and wish to replace every instance of "berry" with "berries" in the `fruit` vector. 


5. replace all 5 letter words in the `words` vector with "five"


6. From the following emails, keep only the first part of the email. In other words, use regex to replace the "\@*something*.net|com" with nothing (`""`).


```r
emails <- c("ahmad@verizon.net", "kenja@sbcglobal.net", 
            "arandal@comcast.net", "seanq@me.com", 
            "vganesh@me.com", "jcholewa@msn.com", 
            "jeffcovey@aol.com", "seebs@me.com", 
            "camenisch@msn.com", "jmcnamara@yahoo.com", 
            "mcraigw@live.com", "conteb@live.com")
```

Your final result should be:

```
## ahmad kenja arandal seanq vganesh jcholewa jeffcovey seebs camenisch jmcnamara mcraigw conteb
```


## combine 

7. create the following tibble:

```r
fruitibble <- tibble::tribble(
                       ~fruit,            ~origin,       ~scientific_name,
                 "Strawberry",           "frANCE",    "fragaria ananassa",
                  "Persimmon",            "China",       "Diospyros kaki",
                   "Honeydew",          "Algeria",         "Cucumis MELO",
                "Dragonfruit",  "Central America", "Selenicereus undatus",
                      "LEMON",            "india",         "citrus Limon",
                 "waterMelon",           "Africa",    "Citrullus lanatus",
                    "Avocado",           "Mexico",     "Persea americana",
                 "Blackberry",          "unknown",       "Rosaceae Rubus",
                     "Banana", "papua new guinea",       "Musa acuminata",
                  "Pineapple",           "Brazil",       "Ananas comosus"
                )
```

8. `Use str_to_*()` function to clean make clean capitalization on the `fruitibble` dataframe. Using tidyverse functions and glue, create a new column called `about` which includes something like "**name** (**scientific name**) is from **origin**". 



9. instead of creating a new column, use the `glue_date()` function to output only the about text into the chunk output. However, make sure your output is sorted by fruit name. 

