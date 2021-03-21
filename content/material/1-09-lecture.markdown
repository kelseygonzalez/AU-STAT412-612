---
title: "Working with strings and `stringr`"		
linktitle: "Lecture	9: Working with strings and `stringr`"
date: "2021-03-22"
start_date: "2021-03-22"
end_date: "2021-03-25"
menu:
  Material:
    parent: Lectures
    weight: 9
type: docs
toc: true
editor_options: 
  markdown: 
    wrap: 72
---

<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>
<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<link href="/rmarkdown-libs/str_view/str_view.css" rel="stylesheet" />
<script src="/rmarkdown-libs/str_view-binding/str_view.js"></script>

# Learning Outcomes

-   Manipulate strings with the stringr package.
-   Employ regular expressions (REGEX) to manipulate strings

# Intro to strings and character vectors

-   In R, strings (also called “characters”) are created and displayed
    within quotes:

``` r
x <- "I am a string!"
x
```

    ## [1] "I am a string!"

``` r
class(x)
```

    ## [1] "character"

-   Anything within quotes is a string, even numbers!

``` r
y <- "3"
class(y)
```

    ## [1] "character"

-   You can have a vector of strings.

``` r
z <- c("I", "am", "a", "string", "vector")
z[2:3]
```

    ## [1] "am" "a"

-   The backslash `"\"` means what is after the backslash is special in
    some way.
-   For example, if you want to put a quotation mark in a string, you
    can “escape” the quotation mark with a backslash.

``` r
a <- "As Michael Scott said, \"I'm not superstitious, but I am a little stitious.\""
a
```

    ## [1] "As Michael Scott said, \"I'm not superstitious, but I am a little stitious.\""

-   `cat()` will print out the string itself.
-   \*`print()` will print out the printed representation of the string
    (with backslashes and all).

``` r
print(x)
```

    ## [1] "I am a string!"

``` r
cat(x)
```

    ## I am a string!

``` r
print(y)
```

    ## [1] "3"

``` r
cat(y)
```

    ## 3

``` r
print(z)
```

    ## [1] "I"      "am"     "a"      "string" "vector"

``` r
cat(z)
```

    ## I am a string vector

``` r
print(a)
```

    ## [1] "As Michael Scott said, \"I'm not superstitious, but I am a little stitious.\""

``` r
cat(a)
```

    ## As Michael Scott said, "I'm not superstitious, but I am a little stitious."

-   `"\n"` represents a new line

``` r
n <- "I'm not superstitious,\nbut I am a little stitious."
cat(n)
```

    ## I'm not superstitious,
    ## but I am a little stitious.

``` r
# what happens if we put spaces around \n? 
```

-   `"\t"` represents a tab

``` r
t <- "I'm not superstitious,\tbut I am a little stitious."
cat(t)
```

    ## I'm not superstitious,   but I am a little stitious.

-   You can add any Unicode character with a `\u` followed by the
    hexadecimal [unicode
    representation](https://en.wikipedia.org/wiki/List_of_Unicode_characters)
    of that character.
-   Be careful about whether knitr will accept it though!

``` r
mu <- "\u00b5"
cat(mu)
```

    ## µ

``` r
cat(c("(","\u2310","\u25A0","\u2022","\u25A0",")"))
```

    ## ( ¬ ¦ • ¦ )

``` r
# http://pages.ucsd.edu/~dkjordan/resources/unicodemaker.html
```

# `stringr`

-   The stringr package has functions to make manipulating strings
    easier - (more user-friendly than base R’s `grep()` and `gsub()`).
-   stringr is part of the tidyverse so you do not have to load it
    separately.

``` r
library(tidyverse)
```

All of stringr’s functions begin with “`str_`,” so in R Studio you can
press tab after typing “`str_`” and a list of possible string
manipulation functions will pop up (in RStudio).

For example, use `str_length()` to get the number of characters in a
string.

``` r
beyonce <- "I am Beyoncé, always."
str_length(beyonce)
```

    ## [1] 21

What about spaces and punctuation marks - they count! What about escaped
characters? The ’’ does not but the character itself does.

``` r
str_length("I am Beyoncé, \nalways.")
```

    ## [1] 22

## Combining Strings with `str_c()`

`str_c()` collapses two strings together:

``` r
x <- "Would I rather be feared or loved?"
y <- "Easy. Both."
z <- "I want people to be afraid of how much they love me."

str_c(x, y, z)
```

    ## [1] "Would I rather be feared or loved?Easy. Both.I want people to be afraid of how much they love me."

The default is to separate strings by nothing, but you can **use `sep`
to change the separator**.

``` r
str_c(x, y, z,  sep = " ")
```

    ## [1] "Would I rather be feared or loved? Easy. Both. I want people to be afraid of how much they love me."

Just like `c()`, `str_c()` can take multiple arguments.

``` r
str_c("Where", "are", "the", "turtles?!", sep = " ")
```

    ## [1] "Where are the turtles?!"

## subsetting substrings with `str_sub()`

`str_sub()` extracts a substring between the location of two characters.

``` r
bankrupt <- "I… Declare… Bankruptcy!"
str_sub(bankrupt, start = 4, end = 10)
```

    ## [1] "Declare"

You often want to use str\_sub when the data is highly structured

``` r
phone <- "800-800-8553"
#first three
str_sub(phone, end = 3)
```

    ## [1] "800"

``` r
# last four
str_sub(phone, start = -4)
```

    ## [1] "8553"

-   Replace substrings with assignment

``` r
str_sub(bankrupt, start = 1, end = 1) <- "We"
bankrupt
```

    ## [1] "We… Declare… Bankruptcy!"

## replacing words with `str_replace()`

If I want to replace a specific pattern of text with another pattern,
`str_replace()` or `str_replace_all()` are very useful.

``` r
str_replace(bankrupt, "We", "I")
```

    ## [1] "I… Declare… Bankruptcy!"

Back with our phone number example, you’ll see there’s a difference
between `str_replace()` or `str_replace_all()`. The first only replaces
the first instance

``` r
phone
```

    ## [1] "800-800-8553"

``` r
str_replace(phone, "800-", "")
```

    ## [1] "800-8553"

``` r
str_replace_all(phone, "800-", "")
```

    ## [1] "8553"

If I only want to change the *second* instance of “800-,” I’ll need to
use a more complicated pattern match. This would require a regular
expression

# Regular Expressions

## Intro

-   Regular expressions (regex or regexp) are a syntax for **pattern
    matching** in strings.

-   Regex structure is used in many different computer languages

-   `str_replace()` and `str_replace_all()` search for a pattern as
    defined by the regex and then replace it (all) with another string.

-   Wherever there is a `pattern` argument in a stringr function, you
    can use regex (to extract strings, get a logical if there is a
    match, etc…).

-   regex includes special characters, e.g., “.” and "“. These must be
    escaped using”" if you want to match their normal value.

## Finding pattern matches with `str_view()` and `str_view_all()`

-   Basic usage: find exact match of a string pattern

``` r
fruit <- c("Apple", "Strawberry", "Banana", "Pear", "Blackberry", "*berry")
str_view(fruit, "an")
```

<div id="htmlwidget-1" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Strawberry<\/li>\n  <li>B<span class='match'>an<\/span>ana<\/li>\n  <li>Pear<\/li>\n  <li>Blackberry<\/li>\n  <li>*berry<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(fruit, "an")
```

<div id="htmlwidget-2" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-2">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Strawberry<\/li>\n  <li>B<span class='match'>an<\/span><span class='match'>an<\/span>a<\/li>\n  <li>Pear<\/li>\n  <li>Blackberry<\/li>\n  <li>*berry<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   A period “`.`” matches any character.
-   A `[:alpha:]` matches any alphabetical character.

``` r
str_view_all(fruit, ".berry")
```

<div id="htmlwidget-3" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-3">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Stra<span class='match'>wberry<\/span><\/li>\n  <li>Banana<\/li>\n  <li>Pear<\/li>\n  <li>Blac<span class='match'>kberry<\/span><\/li>\n  <li><span class='match'>*berry<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(fruit, "[:alpha:]berry")
```

<div id="htmlwidget-4" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-4">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Stra<span class='match'>wberry<\/span><\/li>\n  <li>Banana<\/li>\n  <li>Pear<\/li>\n  <li>Blac<span class='match'>kberry<\/span><\/li>\n  <li>*berry<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   You can “escape” a symbol with two backslashes “`\\.`” to match. If
    you don’t, the asterisk in this case will be interpreted as a
    regular expression command, not a symbol.

``` r
# str_view_all(fruit, "*berry")
str_view_all(fruit, "\\*berry")
```

<div id="htmlwidget-5" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-5">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Strawberry<\/li>\n  <li>Banana<\/li>\n  <li>Pear<\/li>\n  <li>Blackberry<\/li>\n  <li><span class='match'>*berry<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

Exercise: Use one function call to replace `"love"` and `"loved"` with
`"X"` in the following.

``` r
love <- "Would I rather be feared or loved? Easy. Both. I want people to be afraid of how much they love me."
```

``` r
str_view_all(love, "love[:alpha:]*")
```

<div id="htmlwidget-6" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-6">{"x":{"html":"<ul>\n  <li>Would I rather be feared or <span class='match'>loved<\/span>? Easy. Both. I want people to be afraid of how much they <span class='match'>love<\/span> me.<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_replace_all(love, "love[:alpha:]*", "X")
```

    ## [1] "Would I rather be feared or X? Easy. Both. I want people to be afraid of how much they X me."

## Anchoring the regex so search starts at the beginning or at the end of a string

-   You can anchor the regex pattern to begin looking for a match from
    the start (left-to-right) of the string or backwards from the end of
    a string (working-right to left).

-   `^` forces matching to begin **from the start** of a string.

-   `$` forces matching to begin **from the end** of a string.

``` r
str_view(fruit, "^B")
```

<div id="htmlwidget-7" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-7">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Strawberry<\/li>\n  <li><span class='match'>B<\/span>anana<\/li>\n  <li>Pear<\/li>\n  <li><span class='match'>B<\/span>lackberry<\/li>\n  <li>*berry<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view(fruit, "a$")
```

<div id="htmlwidget-8" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-8">{"x":{"html":"<ul>\n  <li>Apple<\/li>\n  <li>Strawberry<\/li>\n  <li>Banan<span class='match'>a<\/span><\/li>\n  <li>Pear<\/li>\n  <li>Blackberry<\/li>\n  <li>*berry<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

Exercise: Use `str_replace()` to replace all four letter words beginning
with an `"a"` with `"foo"` in the following list:

``` r
x <- c("apple", "barn", "ape", "cart", "alas", "pain", "ally")
```

``` r
str_replace(x, "^a...$", "foo")
```

    ## [1] "apple" "barn"  "ape"   "cart"  "foo"   "pain"  "foo"

## Special Characters

There are a lot of regular expression character matches in R and I don’t
expect you to memorize them all - I often have [the
cheatsheet](https://github.com/rstudio/cheatsheets/blob/master/strings.pdf)
open next to me while working. Some important ones you should however be
able to recognize:

| type this:           | to mean this:                   |
|----------------------|---------------------------------|
| \\\\n                | new line                        |
| \\\\s or \[:space:\] | any whitespace                  |
| \\\\d or \[:digit:\] | any digit                       |
| \\\\w \[:alpha:\]    | any word character              |
| \[:punct:\]          | any punctuation                 |
| .                    | every character except new line |

-   We’ll use this character vector for practice:

``` r
phones <- c("Abba: 555-1234", "Anna: 555-0987", "Andy: 555-7654")
```

-   `\\d`: matches any digit

``` r
str_view(phones, "\\d\\d\\d-\\d\\d\\d\\d")
```

<div id="htmlwidget-9" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-9">{"x":{"html":"<ul>\n  <li>Abba: <span class='match'>555-1234<\/span><\/li>\n  <li>Anna: <span class='match'>555-0987<\/span><\/li>\n  <li>Andy: <span class='match'>555-7654<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   `\\s`: matches any white space (e.g. space, tab, newline).

``` r
str_view(phones, "\\s")
```

<div id="htmlwidget-10" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-10">{"x":{"html":"<ul>\n  <li>Abba:<span class='match'> <\/span>555-1234<\/li>\n  <li>Anna:<span class='match'> <\/span>555-0987<\/li>\n  <li>Andy:<span class='match'> <\/span>555-7654<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   `[abc]`: matches `a`, `b`, or `c`.

``` r
str_view(phones, "A[bn][bn]a", "XXXX")
```

<div id="htmlwidget-11" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-11">{"x":{"html":"<ul>\n  <li><span class='match'>Abba<\/span>: 555-1234<\/li>\n  <li><span class='match'>Anna<\/span>: 555-0987<\/li>\n  <li>Andy: 555-7654<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   `[^abc]`: **matches anything except `a`, `b`, or `c`.**
-   Note this is a different use of `^` since it is inside the `[ ]`

``` r
str_view(phones, "A[^b]", "XXXX")
```

<div id="htmlwidget-12" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-12">{"x":{"html":"<ul>\n  <li>Abba: 555-1234<\/li>\n  <li><span class='match'>An<\/span>na: 555-0987<\/li>\n  <li><span class='match'>An<\/span>dy: 555-7654<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   `abc|xyz`: matches either `abc` or `xyz`. This is called
    *alternation*
-   You can use parentheses to control where the alternation occurs.
-   `a(bc|xy)z` matches either `abcz` or `axyz`.

``` r
str_view(phones, "An(na|dy)")
```

<div id="htmlwidget-13" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-13">{"x":{"html":"<ul>\n  <li>Abba: 555-1234<\/li>\n  <li><span class='match'>Anna<\/span>: 555-0987<\/li>\n  <li><span class='match'>Andy<\/span>: 555-7654<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   To ignore case, place a `(?i)` before the regex.

``` r
str_view("AB", "ab")
```

<div id="htmlwidget-14" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-14">{"x":{"html":"<ul>\n  <li>AB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view("AB", "(?i)ab")
```

<div id="htmlwidget-15" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-15">{"x":{"html":"<ul>\n  <li><span class='match'>AB<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

## Repetition using `?`, `+`, `*`, `{n}`, `{n,}`,`{0,n}`, `{n,m}`

-   Can match a pattern multiple times in a row:
-   `?`: **0 or 1**
-   `+`: **1 or more**
-   `*`: **0 or more**

``` r
x <- c("A", "AA", "AAA", "AAAA", "B", "BB")
str_view_all(x, "^A?", "X")
```

<div id="htmlwidget-16" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-16">{"x":{"html":"<ul>\n  <li><span class='match'>A<\/span><\/li>\n  <li><span class='match'>A<\/span>A<\/li>\n  <li><span class='match'>A<\/span>AA<\/li>\n  <li><span class='match'>A<\/span>AAA<\/li>\n  <li><span class='match'><\/span>B<\/li>\n  <li><span class='match'><\/span>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(x, "^A+", "X")
```

<div id="htmlwidget-17" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-17">{"x":{"html":"<ul>\n  <li><span class='match'>A<\/span><\/li>\n  <li><span class='match'>AA<\/span><\/li>\n  <li><span class='match'>AAA<\/span><\/li>\n  <li><span class='match'>AAAA<\/span><\/li>\n  <li>B<\/li>\n  <li>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(x, "^A*", "X")
```

<div id="htmlwidget-18" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-18">{"x":{"html":"<ul>\n  <li><span class='match'>A<\/span><\/li>\n  <li><span class='match'>AA<\/span><\/li>\n  <li><span class='match'>AAA<\/span><\/li>\n  <li><span class='match'>AAAA<\/span><\/li>\n  <li><span class='match'><\/span>B<\/li>\n  <li><span class='match'><\/span>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   A more realistic example:

``` r
str_view_all("color and colour", "colou?r", "X")
```

<div id="htmlwidget-19" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-19">{"x":{"html":"<ul>\n  <li><span class='match'>color<\/span> and <span class='match'>colour<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   **Control exactly how many repetitions** allowed in a match:

-   `{n}`: exactly `n`.

-   `{n,}`: `n` or more.

-   `{0,m}`: at most `m`.

-   `{n,m}`: between `n` and `m`.

``` r
str_view_all(x, "A{2}", "X")
```

<div id="htmlwidget-20" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-20">{"x":{"html":"<ul>\n  <li>A<\/li>\n  <li><span class='match'>AA<\/span><\/li>\n  <li><span class='match'>AA<\/span>A<\/li>\n  <li><span class='match'>AA<\/span><span class='match'>AA<\/span><\/li>\n  <li>B<\/li>\n  <li>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(x, "A{2,}", "X")
```

<div id="htmlwidget-21" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-21">{"x":{"html":"<ul>\n  <li>A<\/li>\n  <li><span class='match'>AA<\/span><\/li>\n  <li><span class='match'>AAA<\/span><\/li>\n  <li><span class='match'>AAAA<\/span><\/li>\n  <li>B<\/li>\n  <li>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(x, "A{0,2}", "X")
```

<div id="htmlwidget-22" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-22">{"x":{"html":"<ul>\n  <li><span class='match'>A<\/span><span class='match'><\/span><\/li>\n  <li><span class='match'>AA<\/span><span class='match'><\/span><\/li>\n  <li><span class='match'>AA<\/span><span class='match'>A<\/span><span class='match'><\/span><\/li>\n  <li><span class='match'>AA<\/span><span class='match'>AA<\/span><span class='match'><\/span><\/li>\n  <li><span class='match'><\/span>B<span class='match'><\/span><\/li>\n  <li><span class='match'><\/span>B<span class='match'><\/span>B<span class='match'><\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_view_all(x, "A{3,4}", "X")
```

<div id="htmlwidget-23" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-23">{"x":{"html":"<ul>\n  <li>A<\/li>\n  <li>AA<\/li>\n  <li><span class='match'>AAA<\/span><\/li>\n  <li><span class='match'>AAAA<\/span><\/li>\n  <li>B<\/li>\n  <li>BB<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

-   Regex is “greedy” and will automatically match the longest string possible.

``` r
str_view("AAAA", "A*",)
```

<div id="htmlwidget-24" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-24">{"x":{"html":"<ul>\n  <li><span class='match'>AAAA<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

Exercise: Create regular expressions to find all words with the
following patterns and replace the patterns with “X”:

1.  Start with three consonants. Test on

``` r
x1 <- c("string", "priority", "value", "distinction")
str_replace_all(x1, "^[^aeiouAEIOU]{3}", "X")
```

    ## [1] "Xing"        "priority"    "value"       "distinction"

There is a lot more to learn about regular expressions what we won’t cover here,
like groups and look arounds. Groups allows you to define which part of the
expression you want to extract or replace and look arounds allow you to define
what follows or precedes the expression. When you need to learn more, there are
many tools online like <https://regex101.com/> to help
you learn. The only important thing to remember with online regular expression
tools is that `r` needs an extra `\` preceding each `\` in other coding
languages.

# more `stringr`

There are a lot of functions to analyze, compare and adjust strings.

## Changing Case

-   `str_to_lower()` and `str_to_upper()` convert all letters to lower
    or capital case.
-   `str_to_sentence` converts all words and letters to sentence
    case. Includes Acronyms
-   `str_to_title` converts the first letter of every word to capital case.

``` r
cause <- "I have cause. It is beCAUSE I hate him."
str_to_lower(cause)
```

    ## [1] "i have cause. it is because i hate him."

``` r
str_to_upper(cause)
```

    ## [1] "I HAVE CAUSE. IT IS BECAUSE I HATE HIM."

``` r
str_to_sentence(cause)
```

    ## [1] "I have cause. It is because i hate him."

``` r
str_to_title(cause)
```

    ## [1] "I Have Cause. It Is Because I Hate Him."

## Detecting matches

-   `str_detect()`: **Returns `TRUE` if a regex pattern matches a string
    and `FALSE` if it does not.** Very useful for filters.

``` r
## Get all John's and Joe's from the Lahman dataset
library(Lahman)
data("People")
People <- People %>% 
  as_tibble()
```

``` r
  People %>%
  filter(str_detect(nameFirst, "^Jo(e|hn)$")) %>%
  select(nameFirst, nameLast) %>% 
  head()
```

    ## # A tibble: 6 x 2
    ##   nameFirst nameLast
    ##   <chr>     <chr>   
    ## 1 John      Abadie  
    ## 2 Joe       Abreu   
    ## 3 Joe       Adams   
    ## 4 Joe       Adcock  
    ## 5 Joe       Agler   
    ## 6 John      Ake

## Counting Matches

-   `str_count()`: **Counts the occurrence of a match within a string**.
-   It counts *non-overlapping* matches

``` r
str_view_all(c("banana", "coco"), "[^aeiou][aeiou]")
```

<div id="htmlwidget-25" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-25">{"x":{"html":"<ul>\n  <li><span class='match'>ba<\/span><span class='match'>na<\/span><span class='match'>na<\/span><\/li>\n  <li><span class='match'>co<\/span><span class='match'>co<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_count(c("banana", "coco"), "[^aeiou][aeiou]")
```

    ## [1] 3 2

``` r
str_view_all("abababa", "aba")
```

<div id="htmlwidget-26" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-26">{"x":{"html":"<ul>\n  <li><span class='match'>aba<\/span>b<span class='match'>aba<\/span><\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_count("abababa", "aba")
```

    ## [1] 2

## Extracting Matches

-   `str_extract()` returns *the first match* for pattern.
-   `str_extract_all()` returns *all matches* but as a list.

``` r
colorstr <- str_c("red", "blue", "yellow", "orange", "brown", sep = "|")
colorstr
```

    ## [1] "red|blue|yellow|orange|brown"

``` r
str_view_all("I like blue and brown and that's it", colorstr)
```

<div id="htmlwidget-27" style="width:960px;height:100%;" class="str_view html-widget"></div>
<script type="application/json" data-for="htmlwidget-27">{"x":{"html":"<ul>\n  <li>I like <span class='match'>blue<\/span> and <span class='match'>brown<\/span> and that's it<\/li>\n<\/ul>"},"evals":[],"jsHooks":[]}</script>

``` r
str_extract("I like blue and brown and that's it", colorstr)
```

    ## [1] "blue"

``` r
str_extract_all("I like blue and brown and that's it", colorstr)
```

    ## [[1]]
    ## [1] "blue"  "brown"

# Combining strings

## `paste` & `paste0`

Base R provides us with a useful tool to collapse strings together (often
referred to as concatenation). However, this tool has limits and is less useful
in data science that glue, which I will teach below.

## `glue`

``` r
# install.packages("glue")

library(glue)
```

    ## 
    ## Attaching package: 'glue'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     collapse

``` r
name <- "Fred"
age <- 50
anniversary <- as.Date("1991-10-12")

glue('My name is {name}, my age next year is {age + 1}, and my anniversary is {format(anniversary, "%A, %B %d, %Y")}.') 
```

    ## My name is Fred, my age next year is 51, and my anniversary is Saturday, October 12, 1991.

``` r
#equivalent in paste:
paste('My name is', name, 'my age next year is', age + 1, 'and my anniversary is', format(anniversary, "%A, %B %d, %Y"), '.')
```

    ## [1] "My name is Fred my age next year is 51 and my anniversary is Saturday, October 12, 1991 ."

glue relies on variable calls to be placed inside of curly brackets `{}` and will interpret the variables within the function.

Use within dataframes:

``` r
employees <- tibble::tribble(
     ~Name,              ~Job,  ~Descriptor,
     "Jim",           "sales",     "quirky",
     "Pam",       "reception",   "artistic",
  "Angela",      "accounting",     "strict",
  "Dwight",           "sales",  "eccentric",
    "Toby", "Human Resources", "monotonous"
  ) 


employees  %>%
  mutate(description = glue("{Name} works in {str_to_title(Job)}"))
```

    ## # A tibble: 5 x 4
    ##   Name   Job             Descriptor description                  
    ##   <chr>  <chr>           <chr>      <glue>                       
    ## 1 Jim    sales           quirky     Jim works in Sales           
    ## 2 Pam    reception       artistic   Pam works in Reception       
    ## 3 Angela accounting      strict     Angela works in Accounting   
    ## 4 Dwight sales           eccentric  Dwight works in Sales        
    ## 5 Toby   Human Resources monotonous Toby works in Human Resources

Use `glue_data` to collapse dataframes into one text output:

``` r
employees %>% 
  glue_data("{Name} is {Descriptor} and works in {str_to_title(Job)} at Dunder Mifflin")
```

    ## Jim is quirky and works in Sales at Dunder Mifflin
    ## Pam is artistic and works in Reception at Dunder Mifflin
    ## Angela is strict and works in Accounting at Dunder Mifflin
    ## Dwight is eccentric and works in Sales at Dunder Mifflin
    ## Toby is monotonous and works in Human Resources at Dunder Mifflin

# More Resources

-   Chapter 14 of [RDS](https://r4ds.had.co.nz/).
-   [R Strings
    Cheathsheet](https://github.com/rstudio/cheatsheets/blob/master/strings.pdf)
-   [R Regex
    Cheatsheet](https://github.com/rstudio/cheatsheets/blob/master/regex.pdf)
-   [Stringr Overview](https://stringr.tidyverse.org/)
-   [glue Overview](https://glue.tidyverse.org/index.html)
