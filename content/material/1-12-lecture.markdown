---
title: "Functions & Control Flow"		
linktitle: "Lecture	12: Functions & Control Flow"
date: "2021-04-05"
start_date: "2021-04-05"
end_date: "2021-04-08"

menu:
  Material:
    parent: Lectures
    weight: 11
type: docs
toc: true
bibliography: "../../static/bib/references.bib"
csl: "../../static/bib/chicago-fullnote-bibliography-no-bib.csl"
---

# Learning Outcomes

1.  Write conditional statements with `if...else` statements and `ifelse()`.
2.  Use `function` to define a new function in R.
    2."Use parameters to pass values into functions.
3.  Write and use functions in R
4.  Use `if` and `stop` for errors
5.  Document functions for easy re-use
6.  Load functions into programs using `source()`

# Control Flow

Often when we’re coding we want to control the flow of our actions. This can be
done by setting actions to occur only if a condition or a set of conditions are
met. Alternatively, we can also set an action to occur a particular number of
times.

There are several ways you can control flow in R. For conditional statements,
the most commonly used approaches are the constructs:

``` r
# if
if (condition is true) {
  perform action
}

# if ... else
if (condition is true) {
  perform action
} else {  # that is, if the condition is false,
  perform alternative action
}
```

Say, for example, that we want R to print a message if a variable `x` has a
particular value:

``` r
x <- 8
if (x >= 10) {
  print("x is greater than or equal to 10")
}
x
```

    ## [1] 8

The print statement does not appear in the console because x is not greater than
10. To print a different message for numbers less than 10, we can add an `else`
statement.

``` r
x <- 8
if (x >= 10) {
  print("x is greater than or equal to 10")
} else {
  print("x is less than 10")
}
```

    ## [1] "x is less than 10"

You can also test multiple conditions by using `else if`.

``` r
x <- 8
if (x >= 10) {
  print("x is greater than or equal to 10")
} else if (x > 5) {
  print("x is greater than 5, but less than 10")
} else {
  print("x is less than 5")
}
```

    ## [1] "x is greater than 5, but less than 10"

**Important:** when R evaluates the condition inside `if()` statements, it is
looking for a logical element, i.e., `TRUE` or `FALSE`. This can cause some
headaches for beginners. For example:

``` r
x  <-  4 == 3
if (x) {
  "4 equals 3"
} else {
  "4 does not equal 3"          
}
```

    ## [1] "4 does not equal 3"

As we can see, the not equal message was printed because the vector x is `FALSE`

``` r
x <- 4 == 3
x
```

    ## [1] FALSE

# DRY - Don’t Repeat Yourself

The [DRY principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) aims
to reduce repetition in software engineering. By writing and using functions to
accomplish a set of instructions multiple times, you reduce the opportunities
for mistakes and often improve performance of the code you write. Functional
programming makes it easy to apply the same analyses to different sets of data,
without excessive copy-paste-update cycles that can introduce hard-to-detect
errors.

# Functions

*What is a function?*  
Functions gather a sequence of operations into a whole, preserving it for
ongoing use. Functions provide:

    - a name we can remember and invoke it by
    - relief from the need to remember the individual operations
    - a defined set of inputs and expected outputs
    - rich connections to the larger programming environment

As the basic building block of most programming languages, user-defined
functions constitute “programming” as much as any single abstraction can. If you
have written a function, you are a computer programmer.

A basic function can involve no specified inputs. It can look something like:

``` r
hi <- function(){
  cat("Hello!")
}
```

When we call on the function `hi`, we get the following output:

``` r
hi()
```

    ## Hello!

Note that we must include parentheses after it because this is a function,
whether or not we are declaring any options.

Let’s update this basic function to now use an input that we provide.

``` r
hi <- function(name){
  cat("Hello!\n")
  cat(name)
}

hi("Delilah")
```

    ## Hello!
    ## Delilah

There are two new parts to the function:  
- a function argument called `name`
- this argument becomes an object inside of the function we can call on

Let’s take this function and use string combination to make this look nicer

``` r
hi <- function(name){
  glue::glue("Hello! {name}!")
}

hi("Delilah")
```

    ## Hello! Delilah!

One thing you may notice if you’re familiar with other programming languages is
that I’m not explicitly calling a `return()`. In R, the `return()` function is
optional: R will automatically return the results of whatever command is
executed on the last line of the function. However, it’s good practice to be
explicit and we will try to follow this practice from now on.

``` r
hi <- function(name){
  hi <- glue::glue("Hello! {name}!")
  return(hi)
}

hi("Delilah")
```

    ## Hello! Delilah!

Even though I have an intermediate object saved in the function (`hi`), notice
the object does not get added into my working environment on the top right pane.
If you want the object to be saved, you’ll need to save the function to a new
object like we have in the past.

``` r
delilah <- hi("Delilah")
```

Let’s finally add in a second option to our function.

``` r
hi <- function(greeting, name, from){
  hi <- glue::glue("{greeting} {name}! - {from}")
  return(hi)
}

hi(greeting = "Hey there",
   name = "Delilah",
   from = "Plain White T's")
```

    ## Hey there Delilah! - Plain White T's

``` r
hi(greeting = "Stay gold",
   name = "Ponyboy",
   from = "S.E. Hinton")
```

    ## Stay gold Ponyboy! - S.E. Hinton

## Fahrenheit to Kelvin

Let’s define a function `fahr_to_kelvin()` that converts temperatures from
Fahrenheit to Kelvin:

``` r
fahr_to_kelvin <- function(temp) {
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}
```

We define `fahr_to_kelvin()` by assigning it to the output of `function`. The
list of argument names are contained within parentheses. Next, the body of the
function–the statements that are executed when it runs–is contained within
curly braces (`{}`). The statements in the body are indented by two spaces. This
makes the code easier to read but does not affect how the code operates. Rstudio
will automatically format this for you.

It is useful to think of creating functions like writing a cookbook. First you
define the “ingredients” that your function needs. In this case, we only need
one ingredient to use our function: “temp.” After we list our ingredients, we
then say what we will do with them, in this case, we are taking our ingredient
and applying a set of mathematical operators to it.

When we call the function, the values we pass to it as arguments are assigned to
those variables so that we can use them inside the function. Inside the
function, we use a return statement to send a result back to whoever asked for
it. As I mentioned, R will automatically print out any code that provides an
output if I don’t have a return statement.

Let’s try running our function.
Calling our own function is no different from calling any other function:

``` r
# freezing point of water
fahr_to_kelvin(32)
```

    ## [1] 273.15

``` r
# boiling point of water
fahr_to_kelvin(212)
```

    ## [1] 373.15

### Exercise

Write a function called `kelvin_to_celsius()` that takes a temperature in Kelvin
and returns that temperature in Celsius.  
- Hint: To convert from Kelvin to Celsius you subtract 273.15

``` r
kelvin_to_celsius <- function(temp) {
  celsius <- temp - 273.15
  return(celsius)
}
```

## Combining functions

The real power of functions comes from mixing, matching and combining them
into ever-larger chunks to get the effect we want. We have been doing this with
functions that are built-in and from packages, but now we can do this ourself:

If we want to convert from Fahrenheit to Celsius, we already have two functions we can use to give us that result. Your first instinct may be to do something like this:

``` r
library(tidyverse)

fahr_to_kelvin(32) %>% 
  kelvin_to_celsius()
```

    ## [1] 0

But we could also define a new function instead:

``` r
fahr_to_celsius <- function(temp_f){
  temp_k <- fahr_to_kelvin(temp_f)
  temp_c <- kelvin_to_celsius(temp_k)
  return(temp_c)
}

fahr_to_celsius(32)
```

    ## [1] 0

Now that we’ve begun to appreciate how writing functions provides an efficient
way to make R code re-usable and modular, we should note that it is important
to ensure that functions only work in their intended use-cases. Checking
function parameters is related to the concept of *defensive programming*.
Defensive programming encourages us to frequently check conditions and throw an
error if something is wrong. These checks are referred to as assertion
statements because we want to assert some condition is `TRUE` before proceeding.
They make it easier to debug because they give us a better idea of where the
errors originate.

## Defensive programming

Let’s start by re-examining `fahr_to_kelvin()`, our function for converting
temperatures from Fahrenheit to Kelvin. It was defined like so:

``` r
fahr_to_kelvin <- function(temp) {
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}
```

For this function to work as intended, the argument `temp` must be a `numeric`
value; otherwise, the mathematical procedure for converting between the two
temperature scales will not work. Right now, the function output is not
particularly useful.

``` r
fahr_to_kelvin("test!")
```

    ## Error in temp - 32: non-numeric argument to binary operator

To create an error message that will help the user understood what went wrong, ,
we can use the function `stop()`. Stop prevents any of the further lines from
running. For example, since the argument `temp` must be a `numeric` vector, we
could check for this condition with an `if` statement and throw an error if the
condition was violated. We could augment our function above like so:

``` r
fahr_to_kelvin <- function(temp) {
  if (!is.numeric(temp)) {
    stop("temp must be a numeric vector.")
  }
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}
```

It still works when given proper input.

``` r
# freezing point of water
fahr_to_kelvin(temp = 32)
```

    ## [1] 273.15

But fails instantly if given improper input.

``` r
# Metric is a character string instead of numeric
fahr_to_kelvin("test!")
```

    ## Error in fahr_to_kelvin("test!"): temp must be a numeric vector.

Note: If a new window pops up, you need to edit your debug settings. Go to `debug` `on error` `message only`.

You can even make the error messages evan more explicit which is great pgoramming practice:

``` r
fahr_to_kelvin <- function(temp) {
  if (!is.numeric(temp)) {
    stop('I am so sorry, but this function only works for numeric input!\n',
         'You have provided an object of class: ', class(temp))
  }
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}

fahr_to_kelvin(32)
```

    ## [1] 273.15

``` r
fahr_to_kelvin("test!")
```

    ## Error in fahr_to_kelvin("test!"): I am so sorry, but this function only works for numeric input!
    ## You have provided an object of class: character

``` r
fahr_to_kelvin(TRUE)
```

    ## Error in fahr_to_kelvin(TRUE): I am so sorry, but this function only works for numeric input!
    ## You have provided an object of class: logical

# Sourcing your functions

Right now, the functions we wrote, are locked up inside our r markdown documnet.
This makes it hard to use outside of this file. In order to make the
`fahr_to_kelvin` and other functions useable elsewhere, we need to move the function to a
separate file and use the `source` command in any script that we would like to
use our function. For the first step, create a new R script through the File
menu or with the keyboard shortcut (Ctrl+Shift+N or Cmd+Shift+N). Let us call
this file `temperature_conversions.R`.

Let’s make sure the script includes information about what is included:

``` r
# Functions for converting temperature data
# Kelsey Gonzalez
# kelseygonzalez@american.edu
# 2021-04-05
```

Let’s paste our finished functions into the script.

``` r
fahr_to_kelvin <- function(temp) {
  if (!is.numeric(temp)) {
    stop('I am so sorry, but this function only works for numeric input!\n',
         'You have provided an object of class: ', class(temp))
  }
  kelvin <- ((temp - 32) * (5 / 9)) + 273.15
  return(kelvin)
}

kelvin_to_celsius <- function(temp) {
  celsius <- temp - 273.15
  return(celsius)
}

fahr_to_celsius <- function(temp_f){
  temp_k <- fahr_to_kelvin(temp_f)
  temp_c <- kelvin_to_celsius(temp_k)
  return(temp_c)
}
```

Now, we will use the `source` function, we tell R to run *all* the code in a specific file. Return to your working `.Rmd` document and add the `source` command to a new code chunk. Set the `file` to the path of your new script.

``` r
source(file = "temperature_conversions.R")
```

An important thing to remember about the `source` function is that it will run *all* the code in that file. We can see this behavior by adding a line before our functions and re-running the `source` function.

First, add this line to the `temperature_conversions.R` file:

``` r
message("Loading functions from temperature_conversions.R")
```

Now rerun your source command. Notice, all of the code gets run, including the
message.

## Tip: Testing and documenting

It’s important to both test functions and document them: Documentation helps
you, and others, understand what the purpose of your function is, and how to use
it, and its important to make sure that your function actually does what you
think.

When you first start out, your workflow will probably look a lot like this:
1. Write a function
2. Comment parts of the function to document its behaviour
3. Load in the source file
4. Experiment with it in the console to make sure it behaves
as you expect
5. Make any necessary bug fixes
6. Rinse and repeat.

If we have time, we can look at the functions we build and better document
them.

There are other more complicated ways to provide documentation and build
functions into packages with things like `roxygen`, `usethis` and `testthat`.
While we won’t go over these in class, you may become interested in package
development and are encouraged to look into these packages and the `More Resources` below.

# Refences

-   [SWC Gapminder - Control Flow Lesson](http://swcarpentry.github.io/r-novice-gapminder/07-control-flow/index.html)
-   [SWC Gapminder - Functions Lesson](http://swcarpentry.github.io/r-novice-gapminder/10-functions/index.html)
-   [Jenny Bryan Functions part 1-3](https://stat545.com/functions-part1.html)
-   [Jeff Oliver’s Introduction to Functional Programming](https://jcoliver.github.io/learn-r/007-intro-functional-programming.html)

# More Resources

-   A deeper dive to [functional programming](http://adv-r.had.co.nz/Functional-programming.html)
-   An *even deeper* dive into [functional programming](http://www.brodrigues.co/fput/)
-   Some [opinions and suggestions](http://adv-r.had.co.nz/Style.html) for naming things like functions (see the ‘Object names’ section)
-   Advanced Functional Programming [from Advanced R](http://adv-r.had.co.nz/Functional-programming.html)
