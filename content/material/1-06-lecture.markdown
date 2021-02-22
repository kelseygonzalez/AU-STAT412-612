---
title: "Advanced Data Wrangling with `dplyr`"		
linktitle: "Lecture	6: Advanced  Data Wrangling with `dplyr`"
date: "2021-02-22"
start_date: "2021-02-22"
end_date: "2021-02-25"
menu:
  Material:
    parent: Lectures
    weight: 6
type: docs
toc: true
---



# Learning Outcomes

- Apply additional dplyr 1.0 functions to manipulate data and data frames for analysis
  + `across()`
  + `case_when()`
  + `rownames_to_columns()`
  + `distinct()`
  + `rowwise()`

- Understand implications of data masking and tidy-select approaches to variables in writing functions with dplyr

# Introduction
- dplyr 1.0 introduced new functions to ease manipulating or summarizing data frames by rows or by columns. We will follow the vignettes for these new capabilities `rowwise()` and `across()`
- Several other dplyr verbs (functions) are often useful for special situations you may face with messy data
- Finally, the tidyverse makes tradeoffs in its approaches to handling variable names that can blur the distinction between variables names *in the environment*, e.g., created with `<-`, versus variable names *in a data frame*, e.g., `df$var_1`. 
- These tradefoffs are designed to make common operations easier but can make programming with dplyr more complicated. 

- We will be using the tidyverse and the dplyr::starwars data frame (see help or `?dplyr::starwars`)
- Load the tidyverse and the starwars data and look at the data.

```r
library(tidyverse)
data(starwars)
head(starwars)
```

```
## # A tibble: 6 x 14
##   name  height  mass hair_color skin_color eye_color birth_year sex   gender
##   <chr>  <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
## 1 Luke~    172    77 blond      fair       blue            19   male  mascu~
## 2 C-3PO    167    75 <NA>       gold       yellow         112   none  mascu~
## 3 R2-D2     96    32 <NA>       white, bl~ red             33   none  mascu~
## 4 Dart~    202   136 none       white      yellow          41.9 male  mascu~
## 5 Leia~    150    49 brown      light      brown           19   fema~ femin~
## 6 Owen~    178   120 brown, gr~ light      blue            52   male  mascu~
## # ... with 5 more variables: homeworld <chr>, species <chr>, films <list>,
## #   vehicles <list>, starships <list>
```

```r
nrow(starwars)
```

```
## [1] 87
```


# Column-wise operations with `across()`
~[]("/img/dplyr_across.png")

- dplyr has had more capability for functions for operating on columns than on rows but it was not always convenient.
- If you want to perform the same operation on multiple columns, copying and pasting could be tedious and error prone:

```r
df %>% 
      group_by(g1, g2) %>% 
      summarise(a = mean(a), b = mean(b), c = mean(c), d = mean(d))
```

- We can now use the `across()` function to write this kind of operation more succinctly and transparently:

```r
df %>% 
      group_by(g1, g2) %>% 
      summarise(across(a:d, mean))
```
      
- `across()` provides new functionality while replacing older functions such as `mutate_if()` or `mutate_at()`    

- We've loaded tidyverse (including dplyr) already.

## Basic Usage of `across()`

- `across` is only used inside other functions, e.g., `summarize()` or `mutate()`
- Like `group_by()` and `rowwise()`, it does not change the data itself but changes how other functions operate on the data.

- `across()` has two primary arguments:
- `.cols = ` selects the columns you want to manipulate (notice the period at the beginning). 
  + It uses tidy selection (like `select()`) so you can pick variables by position, name, and type.
  + The default is `.cols = everything()` so all columns are selected
- `.fns = `, is a function (or a list of functions) you want to apply to each column (.again, note the period at the beginning of the argument name)
  + Examples: `.fns = mean` or `.fns = max`
  + This can also be a purrr style formula like `~ .x / 2`. 
    - The `.x` is the "pronoun" for the columns that get passed to the function
    - We did this in the last `rowwise()` example. 
    - This argument is optional so you can omit it to leave the data  untransformed

## Using `across()` with `summarize()`
- Here are a couple of examples of `across()` in conjunction with its favorite verb, `summarize()`. 

- We use `where()` inside the across to select only those columns of the desired type
- `.fns=` can take a single function
- You can add additional arguments to be passed to the function, e.g., `na.rm = TRUE` ...

```r
starwars %>% 
  summarise(across(where(is.numeric), 
                   .fns = median))
```

```
## # A tibble: 1 x 3
##   height  mass birth_year
##    <int> <dbl>      <dbl>
## 1     NA    NA         NA
```

```r
# Example with argument    
starwars %>% 
  summarise(across(where(is.numeric), 
                   .fns = median, 
                   na.rm = TRUE))
```

```
## # A tibble: 1 x 3
##   height  mass birth_year
##    <int> <dbl>      <dbl>
## 1    180    79         52
```

- The formula approach gives us the ability to combine functions with arguments
    + Using this, you start with the `~` to signify "as a function of" and then put wherever your column name would normally as a `.x`. 

```r
starwars %>% 
          summarise(across(where(is.numeric), 
                           ~ median(.x, na.rm = TRUE)))
```

```
## # A tibble: 1 x 3
##   height  mass birth_year
##    <int> <dbl>      <dbl>
## 1    180    79         52
```

- Let's count how many unique values for character variables using formula style 


```r
# length of unique characters just for hair_color
starwars %>% 
  summarize(unique(hair_color))
```

```
## # A tibble: 13 x 1
##    `unique(hair_color)`
##    <chr>               
##  1 blond               
##  2 <NA>                
##  3 none                
##  4 brown               
##  5 brown, grey         
##  6 black               
##  7 auburn, white       
##  8 auburn, grey        
##  9 white               
## 10 grey                
## 11 auburn              
## 12 blonde              
## 13 unknown
```

```r
starwars %>% 
  summarize(length(unique(hair_color)))
```

```
## # A tibble: 1 x 1
##   `length(unique(hair_color))`
##                          <int>
## 1                           13
```

```r
# summarize all character columns... 
starwars %>% 
  summarise(across(where(is.character), 
                   ~ length(unique(.x))))
```

```
## # A tibble: 1 x 8
##    name hair_color skin_color eye_color   sex gender homeworld species
##   <int>      <int>      <int>     <int> <int>  <int>     <int>   <int>
## 1    87         13         31        15     5      3        49      38
```

- Example with group by species and filter for groups with >1 row and adding a summary that is not inside across to count the rows in each group

```r
starwars %>% 
  group_by(species) %>% 
  filter(n() > 1) %>% 
  summarise(across(c(sex, gender, homeworld), 
                   ~ length(unique(.x))),
                   n=n())
```

```
## # A tibble: 9 x 5
##   species    sex gender homeworld     n
##   <chr>    <int>  <int>     <int> <int>
## 1 Droid        1      2         3     6
## 2 Gungan       1      1         1     3
## 3 Human        2      2        16    35
## 4 Kaminoan     2      2         1     2
## 5 Mirialan     1      1         1     2
## 6 Twi'lek      2      2         1     2
## 7 Wookiee      1      1         1     2
## 8 Zabrak       1      1         2     2
## 9 <NA>         1      1         3     4
```

- Example with group by homeworlds

```r
starwars %>% 
  group_by(homeworld) %>% 
  filter(n() > 1) %>% 
  summarise(across(where(is.numeric), 
                   ~ max(.x, na.rm = TRUE)))    
```

```
## # A tibble: 10 x 4
##    homeworld height  mass birth_year
##    <chr>      <int> <dbl>      <dbl>
##  1 Alderaan     191  79         67  
##  2 Corellia     180  80         29  
##  3 Coruscant    184  50         91  
##  4 Kamino       229  88         31.5
##  5 Kashyyyk     234 136        200  
##  6 Mirial       170  56.2       58  
##  7 Naboo        224  85         82  
##  8 Ryloth       180  55         48  
##  9 Tatooine     202 136        112  
## 10 <NA>         200 140        896
```

- Because across() is usually used in combination with `summarize()` and `mutate()`, **it doesn’t select grouping variables** to avoid accidentally modifying them:
- Example where the grouping variable `g` is not selected, even though it is numeric, so is not summed.

```r
df <- data.frame(g = c(1, 1, 2), x = c(-1, 1, 3), y = c(-1, -4, -9))
df
```

```
##   g  x  y
## 1 1 -1 -1
## 2 1  1 -4
## 3 2  3 -9
```

```r
df %>% 
  group_by(g) %>% 
  summarise(across(where(is.numeric), sum))
```

```
## # A tibble: 2 x 3
##       g     x     y
## * <dbl> <dbl> <dbl>
## 1     1     0    -5
## 2     2     3    -9
```


## Using `across()` with Multiple Functions

- You can transform each variable with more than one function 
- Supply a **named list** of functions in the second argument:

```r
# Example with no list but argument
starwars %>% 
  summarise(across(where(is.numeric),
                   .fns = list(median, mean), 
                    na.rm = TRUE))  
```

```
## # A tibble: 1 x 6
##   height_1 height_2 mass_1 mass_2 birth_year_1 birth_year_2
##      <int>    <dbl>  <dbl>  <dbl>        <dbl>        <dbl>
## 1      180     174.     79   97.3           52         87.6
```

```r
# Example with list and argument
starwars %>% 
  summarise(across(where(is.numeric),
                   .fns = list(median = median, mean = mean), 
                    na.rm = TRUE))  
```

```
## # A tibble: 1 x 6
##   height_median height_mean mass_median mass_mean birth_year_medi~
##           <int>       <dbl>       <dbl>     <dbl>            <dbl>
## 1           180        174.          79      97.3               52
## # ... with 1 more variable: birth_year_mean <dbl>
```

### Controlling  Names
In the last case where we wanted to create a median and mean across all numeric variables, you'll notice that the new variable names were always `{name_of_variable}_{mean/median}`. This is the default behavior of across - the name, an underscore, and the name of the function from the named list provided. To customize how things are named, you can use `glue` syntax (we'll cover what glue is in a few weeks) and the `.names` argument. 
+ `{.fn}` will refer to the name of the function you used
+ `{.col}` will refer to the name of the column


```r
#change to {function}_{column}
starwars %>% 
  summarise(across(where(is.numeric),
                   .fns = list(median = median, mean = mean), 
                    na.rm = TRUE,
                   .names = "{.fn}_{.col}"))  
```

```
## # A tibble: 1 x 6
##   median_height mean_height median_mass mean_mass median_birth_ye~
##           <int>       <dbl>       <dbl>     <dbl>            <dbl>
## 1           180        174.          79      97.3               52
## # ... with 1 more variable: mean_birth_year <dbl>
```

```r
#change to {function}_{column}
starwars %>% 
  summarise(across(where(is.numeric),
                   .fns = list(median = median, mean = mean), 
                    na.rm = TRUE,
                   .names = "The {.fn} of {.col}"))  
```

```
## # A tibble: 1 x 6
##   `The median of ~ `The mean of he~ `The median of ~ `The mean of ma~
##              <int>            <dbl>            <dbl>            <dbl>
## 1              180             174.               79             97.3
## # ... with 2 more variables: `The median of birth_year` <dbl>, `The mean of
## #   birth_year` <dbl>
```

## Gotchas - Order Matters

- Be careful when combining numeric summaries with `is.numeric()`:


```r
df <- data.frame(x = c(1, 2, 3), y = c(1, 4, 9))
df
```

```
##   x y
## 1 1 1
## 2 2 4
## 3 3 9
```

```r
df %>% 
  summarise(n = n(), across(where(is.numeric), sd))
```

```
##    n x        y
## 1 NA 1 4.041452
```
    
- Here n became `NA` because n is numeric, so the `across()` computes its standard deviation, and the standard deviation of 3 (a constant) is `NA`. 
- You probably want to compute `n()` last to avoid this problem:


```r
df %>% 
  summarise(across(where(is.numeric), sd), n = n())
```

```
##   x        y n
## 1 1 4.041452 3
```
### Some other examples 

- Example: Find all rows where no variable has missing values:

```r
starwars %>% filter(across(everything(), ~ !is.na(.x)))
```

```
## # A tibble: 29 x 14
##    name  height  mass hair_color skin_color eye_color birth_year sex   gender
##    <chr>  <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
##  1 Luke~    172    77 blond      fair       blue            19   male  mascu~
##  2 Dart~    202   136 none       white      yellow          41.9 male  mascu~
##  3 Leia~    150    49 brown      light      brown           19   fema~ femin~
##  4 Owen~    178   120 brown, gr~ light      blue            52   male  mascu~
##  5 Beru~    165    75 brown      light      blue            47   fema~ femin~
##  6 Bigg~    183    84 black      light      brown           24   male  mascu~
##  7 Obi-~    182    77 auburn, w~ fair       blue-gray       57   male  mascu~
##  8 Anak~    188    84 blond      fair       blue            41.9 male  mascu~
##  9 Chew~    228   112 brown      unknown    blue           200   male  mascu~
## 10 Han ~    180    80 brown      fair       brown           29   male  mascu~
## # ... with 19 more rows, and 5 more variables: homeworld <chr>, species <chr>,
## #   films <list>, vehicles <list>, starships <list>
```

- For some verbs, like `group_by()`, `count()` and `distinct()`, you can omit the summary functions:
- Example: Find all distinct rows for variables with the word color in the name

```r
starwars %>% distinct(across(contains("color"))) %>% 
  arrange(hair_color, skin_color)
```

```
## # A tibble: 67 x 3
##    hair_color    skin_color eye_color
##    <chr>         <chr>      <chr>    
##  1 auburn        fair       blue     
##  2 auburn, grey  fair       blue     
##  3 auburn, white fair       blue-gray
##  4 black         blue, grey yellow   
##  5 black         brown      brown    
##  6 black         dark       brown    
##  7 black         dark       dark     
##  8 black         fair       brown    
##  9 black         light      brown    
## 10 black         tan        brown    
## # ... with 57 more rows
```

- Example: Count all combinations of variables with a given pattern:

```r
starwars %>% count(across(contains("color")), sort = TRUE) %>% 
  arrange(hair_color, skin_color)
```

```
## # A tibble: 67 x 4
##    hair_color    skin_color eye_color     n
##    <chr>         <chr>      <chr>     <int>
##  1 auburn        fair       blue          1
##  2 auburn, grey  fair       blue          1
##  3 auburn, white fair       blue-gray     1
##  4 black         blue, grey yellow        1
##  5 black         brown      brown         1
##  6 black         dark       brown         3
##  7 black         dark       dark          1
##  8 black         fair       brown         2
##  9 black         light      brown         1
## 10 black         tan        brown         2
## # ... with 57 more rows
```
- `across()` doesn’t work with `select()` or `rename()` because they already use tidy select syntax; 


### Exercise

- Calculate the median for each numeric variable for each species and gender 

```r
starwars %>% 
  group_by(species, gender) %>% 
  summarise(across(where(is.numeric), 
                   ~ median(.x, na.rm = TRUE)))
```

```
## # A tibble: 42 x 5
## # Groups:   species [38]
##    species   gender    height  mass birth_year
##    <chr>     <chr>      <dbl> <dbl>      <dbl>
##  1 Aleena    masculine     79  15           NA
##  2 Besalisk  masculine    198 102           NA
##  3 Cerean    masculine    198  82           92
##  4 Chagrian  masculine    196  NA           NA
##  5 Clawdite  feminine     168  55           NA
##  6 Droid     feminine      96  NA           NA
##  7 Droid     masculine    132  53.5         33
##  8 Dug       masculine    112  40           NA
##  9 Ewok      masculine     88  20            8
## 10 Geonosian masculine    183  80           NA
## # ... with 32 more rows
```

- Calculate the min and max for each numeric variable other than birth year for each species and gender and count how many are in each group and sort from largest to smallest count.    

```r
starwars %>% 
  group_by(species, gender) %>% 
  summarise(across(where(is.numeric) & !birth_year, 
                   .fns = list(min = ~ min(.x, na.rm = TRUE), 
                               max = ~ max(.x, na.rm = TRUE))), 
            n=n()) %>% 
  arrange(desc(n))
```

```
## # A tibble: 42 x 7
## # Groups:   species [38]
##    species  gender    height_min height_max mass_min mass_max     n
##    <chr>    <chr>          <int>      <int>    <dbl>    <dbl> <int>
##  1 Human    masculine        170        202       75    136      26
##  2 Human    feminine         150        167       45     75       9
##  3 Droid    masculine         96        200       32    140       5
##  4 <NA>     <NA>             178        183       48     48       4
##  5 Gungan   masculine        196        224       66     82       3
##  6 Mirialan feminine         166        170       50     56.2     2
##  7 Wookiee  masculine        228        234      112    136       2
##  8 Zabrak   masculine        171        175       80     80       2
##  9 Aleena   masculine         79         79       15     15       1
## 10 Besalisk masculine        198        198      102    102       1
## # ... with 32 more rows
```

# `case_when()`
~[]("/img/dplyr_case_when_sm.png")

- This function allows you to vectorize (and replace) multiple `if_else()` statements in a succinct and clear manner.
- The syntax is `case_when(...)`
- The `dot dot dots` are a placeholder for a series of two-side formulas
  + The Left hand side (LHS) determines which variables match a given case - this must return a logical vector
  + The Right hand side (RHS) provides the new or replacement value and all have to be of the same type of vector
  + Both LHS and RHS may be of length either 1 or `n`
  + you always end with a case of TRUE for when all of the other cases are FALSE

- Example of a vectorized if - else

```r
x <- 1:16

case_when(
  x < 5 ~ "less than 5",
  x < 10 ~ "less than 10",
  TRUE ~ as.character(x)
)
```

```
##  [1] "less than 5"  "less than 5"  "less than 5"  "less than 5"  "less than 10"
##  [6] "less than 10" "less than 10" "less than 10" "less than 10" "10"          
## [11] "11"           "12"           "13"           "14"           "15"          
## [16] "16"
```

```r
# From https://www.hackerrank.com/challenges/fizzbuzz/problem
case_when(
  x %% 15 == 0 ~ "fizz buzz",
  x %% 3 == 0 ~ "fizz",
  x %% 5 == 0 ~ "buzz",
  TRUE ~ as.character(x)
)
```

```
##  [1] "1"         "2"         "fizz"      "4"         "buzz"      "fizz"     
##  [7] "7"         "8"         "fizz"      "buzz"      "11"        "fizz"     
## [13] "13"        "14"        "fizz buzz" "16"
```

- Like an if statement, the arguments are evaluated in order, so you must proceed from the most specific to the most general. 
- This won't work:


```r
case_when(
  TRUE ~ as.character(x),
  x %%  5 == 0 ~ "fizz",
  x %%  7 == 0 ~ "buzz",
  x %% 35 == 0 ~ "fizz buzz"
)
```

```
##  [1] "1"  "2"  "3"  "4"  "5"  "6"  "7"  "8"  "9"  "10" "11" "12" "13" "14" "15"
## [16] "16"
```
    
- `case_when()` is **particularly useful inside `mutate()`** when you want to create a new variable that relies on a complex combination of existing variables     

```r
starwars %>%
  select(name:mass, gender, species) %>%
  mutate(
    height_cat = case_when(
      height > 191 ~ "tall",
      height < 167 ~ "short",
      TRUE  ~ "average"
    )
  )
```

```
## # A tibble: 87 x 6
##    name               height  mass gender    species height_cat
##    <chr>               <int> <dbl> <chr>     <chr>   <chr>     
##  1 Luke Skywalker        172    77 masculine Human   average   
##  2 C-3PO                 167    75 masculine Droid   average   
##  3 R2-D2                  96    32 masculine Droid   short     
##  4 Darth Vader           202   136 masculine Human   tall      
##  5 Leia Organa           150    49 feminine  Human   short     
##  6 Owen Lars             178   120 masculine Human   average   
##  7 Beru Whitesun lars    165    75 feminine  Human   short     
##  8 R5-D4                  97    32 masculine Droid   short     
##  9 Biggs Darklighter     183    84 masculine Human   average   
## 10 Obi-Wan Kenobi        182    77 masculine Human   average   
## # ... with 77 more rows
```

```r
starwars %>%
  select(name:mass, gender, species) %>%
  mutate(
    height_cat = case_when(
      height > quantile(height, 3/4, na.rm = TRUE) ~ "tall",
      height < quantile(height, 1/4, na.rm = TRUE) ~ "short",
      TRUE  ~ "average"
    )
  ) 
```

```
## # A tibble: 87 x 6
##    name               height  mass gender    species height_cat
##    <chr>               <int> <dbl> <chr>     <chr>   <chr>     
##  1 Luke Skywalker        172    77 masculine Human   average   
##  2 C-3PO                 167    75 masculine Droid   average   
##  3 R2-D2                  96    32 masculine Droid   short     
##  4 Darth Vader           202   136 masculine Human   tall      
##  5 Leia Organa           150    49 feminine  Human   short     
##  6 Owen Lars             178   120 masculine Human   average   
##  7 Beru Whitesun lars    165    75 feminine  Human   short     
##  8 R5-D4                  97    32 masculine Droid   short     
##  9 Biggs Darklighter     183    84 masculine Human   average   
## 10 Obi-Wan Kenobi        182    77 masculine Human   average   
## # ... with 77 more rows
```

```r
# But this can be even more complicated... 
starwars %>%
  select(name:mass, gender, species) %>%
  mutate(
    type = case_when(
      height > 200 | mass > 200 ~ "large",
      species == "Droid"        ~ "robot",
      TRUE                      ~ "other"
    )
  )
```

```
## # A tibble: 87 x 6
##    name               height  mass gender    species type 
##    <chr>               <int> <dbl> <chr>     <chr>   <chr>
##  1 Luke Skywalker        172    77 masculine Human   other
##  2 C-3PO                 167    75 masculine Droid   robot
##  3 R2-D2                  96    32 masculine Droid   robot
##  4 Darth Vader           202   136 masculine Human   large
##  5 Leia Organa           150    49 feminine  Human   other
##  6 Owen Lars             178   120 masculine Human   other
##  7 Beru Whitesun lars    165    75 feminine  Human   other
##  8 R5-D4                  97    32 masculine Droid   robot
##  9 Biggs Darklighter     183    84 masculine Human   other
## 10 Obi-Wan Kenobi        182    77 masculine Human   other
## # ... with 77 more rows
```
  
## `tibble::rownames_to_columns()` 
- You many occasionally see data sets where there are row names. 
- This is allowed but not common with data frames as row names are removed when using `[...]`
- Tidy data (a tibble) does not use row_names so they are stripped when coerced to a tibble
- dplyr had a function `add_rownames()` but that has been replaced (deprecated) by the `tibble::rownames_to_columns()`
- Generally, it is best to avoid row names, because they are basically a character column with different semantics than every other column.
- To detect if a data frame has row_names use `has_rownames()`

```r
head(state.x77)
```

```
##            Population Income Illiteracy Life Exp Murder HS Grad Frost   Area
## Alabama          3615   3624        2.1    69.05   15.1    41.3    20  50708
## Alaska            365   6315        1.5    69.31   11.3    66.7   152 566432
## Arizona          2212   4530        1.8    70.55    7.8    58.1    15 113417
## Arkansas         2110   3378        1.9    70.66   10.1    39.9    65  51945
## California      21198   5114        1.1    71.71   10.3    62.6    20 156361
## Colorado         2541   4884        0.7    72.06    6.8    63.9   166 103766
```

```r
str(state.x77)
```

```
##  num [1:50, 1:8] 3615 365 2212 2110 21198 ...
##  - attr(*, "dimnames")=List of 2
##   ..$ : chr [1:50] "Alabama" "Alaska" "Arizona" "Arkansas" ...
##   ..$ : chr [1:8] "Population" "Income" "Illiteracy" "Life Exp" ...
```

```r
has_rownames(as_tibble(state.x77))
```

```
## [1] FALSE
```

```r
has_rownames(state.x77)
```

```
## [1] FALSE
```

```r
has_rownames(as.data.frame(state.x77))
```

```
## [1] TRUE
```

- To convert the row names to a variable, convert to a data.frame is necessary, and use `rownames_to_column()`
- e.g., `rownames_to_column(.data, var = "rowname")`
- Then convert to a tibble using `as_tibble()`

```r
rownames_to_column(as.data.frame(state.x77), "State") %>% 
  str() %>% 
  as_tibble()
```

```
## 'data.frame':	50 obs. of  9 variables:
##  $ State     : chr  "Alabama" "Alaska" "Arizona" "Arkansas" ...
##  $ Population: num  3615 365 2212 2110 21198 ...
##  $ Income    : num  3624 6315 4530 3378 5114 ...
##  $ Illiteracy: num  2.1 1.5 1.8 1.9 1.1 0.7 1.1 0.9 1.3 2 ...
##  $ Life Exp  : num  69 69.3 70.5 70.7 71.7 ...
##  $ Murder    : num  15.1 11.3 7.8 10.1 10.3 6.8 3.1 6.2 10.7 13.9 ...
##  $ HS Grad   : num  41.3 66.7 58.1 39.9 62.6 63.9 56 54.6 52.6 40.6 ...
##  $ Frost     : num  20 152 15 65 20 166 139 103 11 60 ...
##  $ Area      : num  50708 566432 113417 51945 156361 ...
```

```
## # A tibble: 0 x 0
```

### Exercise

- Check if the `mtcars` data set has row names. If so, convert the rownames to a column named `car` and convert to a tibble

```r
has_rownames(mtcars)
```

```
## [1] TRUE
```

```r
rownames_to_column(mtcars, var = "car") %>% 
  as_tibble()
```

```
## # A tibble: 32 x 12
##    car           mpg   cyl  disp    hp  drat    wt  qsec    vs    am  gear  carb
##    <chr>       <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
##  1 Mazda RX4    21       6  160    110  3.9   2.62  16.5     0     1     4     4
##  2 Mazda RX4 ~  21       6  160    110  3.9   2.88  17.0     0     1     4     4
##  3 Datsun 710   22.8     4  108     93  3.85  2.32  18.6     1     1     4     1
##  4 Hornet 4 D~  21.4     6  258    110  3.08  3.22  19.4     1     0     3     1
##  5 Hornet Spo~  18.7     8  360    175  3.15  3.44  17.0     0     0     3     2
##  6 Valiant      18.1     6  225    105  2.76  3.46  20.2     1     0     3     1
##  7 Duster 360   14.3     8  360    245  3.21  3.57  15.8     0     0     3     4
##  8 Merc 240D    24.4     4  147.    62  3.69  3.19  20       1     0     4     2
##  9 Merc 230     22.8     4  141.    95  3.92  3.15  22.9     1     0     4     2
## 10 Merc 280     19.2     6  168.   123  3.92  3.44  18.3     1     0     4     4
## # ... with 22 more rows
```

## `distinct()`
- We used `distinct()` earlier to remove duplicate entries in a group by grouping. 
- `distinct()` subsets only unique/distinct rows from a data frame. 
- Rows are a subset of the input but appear in the same order.
- Columns are not modified by default
- Groups are not modified.
- Data frame attributes are preserved.
- Example with 

```r
starwars %>% 
  distinct(homeworld) 
```

```
## # A tibble: 49 x 1
##    homeworld 
##    <chr>     
##  1 Tatooine  
##  2 Naboo     
##  3 Alderaan  
##  4 Stewjon   
##  5 Eriadu    
##  6 Kashyyyk  
##  7 Corellia  
##  8 Rodia     
##  9 Nal Hutta 
## 10 Bestine IV
## # ... with 39 more rows
```

```r
starwars %>% 
  distinct(homeworld, species)
```

```
## # A tibble: 58 x 2
##    homeworld species
##    <chr>     <chr>  
##  1 Tatooine  Human  
##  2 Tatooine  Droid  
##  3 Naboo     Droid  
##  4 Alderaan  Human  
##  5 Stewjon   Human  
##  6 Eriadu    Human  
##  7 Kashyyyk  Wookiee
##  8 Corellia  Human  
##  9 Rodia     Rodian 
## 10 Nal Hutta Hutt   
## # ... with 48 more rows
```

```r
#Very similar to count()... 
starwars %>% 
  count(homeworld, species)
```

```
## # A tibble: 58 x 3
##    homeworld      species       n
##    <chr>          <chr>     <int>
##  1 Alderaan       Human         3
##  2 Aleen Minor    Aleena        1
##  3 Bespin         Human         1
##  4 Bestine IV     Human         1
##  5 Cato Neimoidia Neimodian     1
##  6 Cerea          Cerean        1
##  7 Champala       Chagrian      1
##  8 Chandrila      Human         1
##  9 Concord Dawn   Human         1
## 10 Corellia       Human         2
## # ... with 48 more rows
```

```r
# Example from a "student hours question on gapminder... 
library(gapminder)
data(gapminder)
gapminder %>% 
  distinct(continent, country) %>% 
  count(continent)
```

```
## # A tibble: 5 x 2
##   continent     n
## * <fct>     <int>
## 1 Africa       52
## 2 Americas     25
## 3 Asia         33
## 4 Europe       30
## 5 Oceania       2
```


# Row-wise operations with `rowwise()`
- Before version 1.0, dplyr did not have special capabilities for operating on subsets of rows. You had to use for-loops for operating across rows or subsets of rows.
- dplyr 1.0 added the new verb `rowwise()` to create multiple one-row data frames out of an existing data frame
- These row-wise data frames are "virtual" subsets of the original data frame - - You can operate on each subset data frame as if it were its own data frame.
- We will discuss a common use case: computing aggregates across multiple columns within a row

## Creating row-wise data frames
- Row-wise operations require a special type of grouping where each group consists of a **single row**. 
- You create this grouping using `rowwise()`
- Like `group_by()`, `rowwise()` doesn’t really do anything itself; it just changes how the other dplyr verbs work. 
- For example, compare the results of `mutate()` in the following code:

```r
fruits <- tribble(
  ~"fruit", ~"height_1", ~"height_2", ~"height_3", ~"width", ~"weight",
  "Banana", 4, 4.2, 3.5, 1, 0.5,
  "Strawberry", 1, .9, 1.2, 1, .25,
  "Pineapple", 18, 17.7, 19.2, 6, 3)
fruits
```

```
## # A tibble: 3 x 6
##   fruit      height_1 height_2 height_3 width weight
##   <chr>         <dbl>    <dbl>    <dbl> <dbl>  <dbl>
## 1 Banana            4      4.2      3.5     1   0.5 
## 2 Strawberry        1      0.9      1.2     1   0.25
## 3 Pineapple        18     17.7     19.2     6   3
```

```r
# mean across all values in all rows
fruits %>% 
  mutate(height_mean = mean(c(height_1, height_2, height_3))) 
```

```
## # A tibble: 3 x 7
##   fruit      height_1 height_2 height_3 width weight height_mean
##   <chr>         <dbl>    <dbl>    <dbl> <dbl>  <dbl>       <dbl>
## 1 Banana            4      4.2      3.5     1   0.5         7.74
## 2 Strawberry        1      0.9      1.2     1   0.25        7.74
## 3 Pineapple        18     17.7     19.2     6   3           7.74
```

```r
# mean across all values in each row
fruits %>% 
  rowwise(fruit) %>% 
  mutate(height_mean = mean(c(height_1, height_2, height_3)))
```

```
## # A tibble: 3 x 7
## # Rowwise:  fruit
##   fruit      height_1 height_2 height_3 width weight height_mean
##   <chr>         <dbl>    <dbl>    <dbl> <dbl>  <dbl>       <dbl>
## 1 Banana            4      4.2      3.5     1   0.5         3.9 
## 2 Strawberry        1      0.9      1.2     1   0.25        1.03
## 3 Pineapple        18     17.7     19.2     6   3          18.3
```

## Per-row Summary Statistics
- `dplyr::summarize()` makes it really easy to summarize values across the rows within one column. 
- We can combine `rowwise()` and `summarize()` to make it easy to summarize values *across columns within one row*. 
- We’ll start by making a little dataset:


```r
df <- tibble(id = 1:6, w = 10:15, x = 20:25, y = 30:35, z = 40:45)
df
```

```
## # A tibble: 6 x 5
##      id     w     x     y     z
##   <int> <int> <int> <int> <int>
## 1     1    10    20    30    40
## 2     2    11    21    31    41
## 3     3    12    22    32    42
## 4     4    13    23    33    43
## 5     5    14    24    34    44
## 6     6    15    25    35    45
```
- Let’s say we want compute the sum of w, x, y, and z for each row. 
- We start by making a row-wise data frame:
- We then use `mutate()` to add a new column to each row, or.
- Just use `summarise()` to return the summary:

```r
rf <- df %>% rowwise(id)
# mutate to add new column for each row
rf %>% mutate(total = sum(c(w, x, y, z)))
```

```
## # A tibble: 6 x 6
## # Rowwise:  id
##      id     w     x     y     z total
##   <int> <int> <int> <int> <int> <int>
## 1     1    10    20    30    40   100
## 2     2    11    21    31    41   104
## 3     3    12    22    32    42   108
## 4     4    13    23    33    43   112
## 5     5    14    24    34    44   116
## 6     6    15    25    35    45   120
```

```r
# summarize without mutate
rf %>% summarise(total = sum(c(w, x, y, z)), .groups= "drop")
```

```
## # A tibble: 6 x 2
##      id total
##   <int> <int>
## 1     1   100
## 2     2   104
## 3     3   108
## 4     4   112
## 5     5   116
## 6     6   120
```

- If you have a lot of variables, you can use `c_across()` to succinctly select many variables (`c_across()` uses tidy select helpers)
- The `where(is.numeric())` ensures we only select numeric columns


```r
rf %>% mutate(total = sum(c_across(w:z)))
```

```
## # A tibble: 6 x 6
## # Rowwise:  id
##      id     w     x     y     z total
##   <int> <int> <int> <int> <int> <int>
## 1     1    10    20    30    40   100
## 2     2    11    21    31    41   104
## 3     3    12    22    32    42   108
## 4     4    13    23    33    43   112
## 5     5    14    24    34    44   116
## 6     6    15    25    35    45   120
```

```r
rf %>% mutate(total = sum(c_across(where(is.numeric))))
```

```
## # A tibble: 6 x 6
## # Rowwise:  id
##      id     w     x     y     z total
##   <int> <int> <int> <int> <int> <int>
## 1     1    10    20    30    40   100
## 2     2    11    21    31    41   104
## 3     3    12    22    32    42   108
## 4     4    13    23    33    43   112
## 5     5    14    24    34    44   116
## 6     6    15    25    35    45   120
```

```r
# If we want to use our fruits example... 
fruits %>% 
  rowwise(fruit) %>% 
  mutate(height_mean = mean(c_across(contains("height"))))
```

```
## # A tibble: 3 x 7
## # Rowwise:  fruit
##   fruit      height_1 height_2 height_3 width weight height_mean
##   <chr>         <dbl>    <dbl>    <dbl> <dbl>  <dbl>       <dbl>
## 1 Banana            4      4.2      3.5     1   0.5         3.9 
## 2 Strawberry        1      0.9      1.2     1   0.25        1.03
## 3 Pineapple        18     17.7     19.2     6   3          18.3
```
- so c_across is a _rowwise_ version of the function we learned earlier, across. 

- You could combine c_across with column-wise across to compute the proportion of the total for each column:

```r
rf %>% #our row-wise data frame
  mutate(total = sum(c_across(w:z))) %>% #total each row
  ungroup() %>% # ungroup the rows
  mutate(across(w:z, ~ .x / total)) # the .x represents each column
```

```
## # A tibble: 6 x 6
##      id     w     x     y     z total
##   <int> <dbl> <dbl> <dbl> <dbl> <int>
## 1     1 0.1   0.2   0.3   0.4     100
## 2     2 0.106 0.202 0.298 0.394   104
## 3     3 0.111 0.204 0.296 0.389   108
## 4     4 0.116 0.205 0.295 0.384   112
## 5     5 0.121 0.207 0.293 0.379   116
## 6     6 0.125 0.208 0.292 0.375   120
```


### Exercise
- Let's create a new variable for the starwars data frame with the maximum of the height, mass, or birth year for each starwars character. Who has the maximum of all the characters?

```r
starwars %>% 
  filter(!is.na(height), !is.na(mass),) %>%
  rowwise() %>% 
  mutate(max_a = max(height, mass, na.rm = TRUE)) %>% 
  relocate(max_a) %>% 
  ungroup() %>% 
  select(name, where(is.numeric)) %>% 
  slice_max(max_a) 
```

```
## # A tibble: 1 x 5
##   name                  max_a height  mass birth_year
##   <chr>                 <dbl>  <int> <dbl>      <dbl>
## 1 Jabba Desilijic Tiure  1358    175  1358        600
```

```r
starwars %>% 
  filter(!is.na(height), !is.na(mass)) %>%
  rowwise() %>% 
  mutate(max_a = max(height, mass, na.rm = TRUE)) %>% 
  relocate(max_a) %>% 
  ungroup() %>% 
  select(name, where(is.numeric)) %>% 
  filter(max_a == max(max_a))
```

```
## # A tibble: 1 x 5
##   name                  max_a height  mass birth_year
##   <chr>                 <dbl>  <int> <dbl>      <dbl>
## 1 Jabba Desilijic Tiure  1358    175  1358        600
```


## Bottom Line
- Be aware of the issues that can arise if you try to write complex functions where you are passing arguments with names of variables from the environment, as opposed to referring to variables within a data frame.
- There are solutions but they require additional effort and understanding.

- **References**
  - Chapter 5 of [RDS](https://r4ds.had.co.nz/)
  - [Data Transformation Cheat Sheet](https://github.com/rstudio/cheatsheets/blob/master/data-transformation.pdf).
  - [Row-Wise Operations](https://dplyr.tidyverse.org/articles/rowwise.html).
  - [Column-Wise Operations](https://dplyr.tidyverse.org/articles/colwise.html).
  - [Programming with dplyr](https://dplyr.tidyverse.org/articles/programming.html)
