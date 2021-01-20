---
title: "Intro to R & Data Science"
linktitle: "Lecture 1: Intro to R & Data Science"
date: "2021-01-21"
start_date: "2021-01-21"
end_date: "2021-01-25"
menu:
  material:
    parent: Lectures
    weight: 1
type: docs
toc: true
bibliography: "../../static/bib/references.bib"
csl: "../../static/bib/chicago-fullnote-bibliography-no-bib.csl"
---

# Intro to R & Data Science

Learning Outcomes

-   Understand Data Science as the context for this course  
-   Understand R in the context of data science.

## What is Data Science?

-   Coined in 2001, “*Data science* is a discipline that incorporates varying degrees of Data Engineering, Scientific Method, Math, Statistics, Advanced Computing, Visualization, Hacker mindset, and Domain Expertise.” William S Cleveland[^1]

-   “Data science, or data-driven science, combines different fields of work in statistics and computation to interpret data for decision-making purposes.” Caroline Banton[^2]

-   “Data science is a multi-disciplinary field that uses scientific methods, processes, algorithms and systems to extract knowledge and insights from structured and unstructured data.”

-   **“Data Scientist: The Sexiest Job of the 21st Century”** THDJ Patil and T Davenport[^3]

## Components of Data Science

<img src="/img/ds-venn.jpg" style="width:50.0%" />

-   Statistics
-   Domain Knowledge
-   Computation

## Statistics

-   Inferring general properties given data.
-   Causal inference.
-   Modeling (descriptive and predictive).
-   Quantifying uncertainty.
-   STAT 514, Statistical Methods, STAT 615 (Regression), STAT 627 (Machine Learning),
-   Most of the STAT curriculum is applicable.

## Domain Knowledge

-   Expertise in an area of application
    -   e.g., biology, psychology, economics, chemistry, etc..
-   Allows you to understand data in context of the area and/or decision to be made.
-   Lets you ask interesting questions.
-   Lets you spot problems with existing analysis pipelines.
-   Various “Tracks” in the data science program.

## Computation – This class

-   Data import
-   Data preparation
-   Data exploration
-   Data transformation
-   Data visualization
-   STAT 612 (R programming), STAT 613 (Data Science), most of the CS curriculum.

# Various Professions

## What makes a data scientist?

-   People in diverse professions use these three skills to analyze data.
-   Professions often differ by their level of expertise or interest in each skill.
-   Data Science projects usually a “team activity”

<img src="/material/1-01-lecture_files/figure-html/unnamed-chunk-1-1.png" width="672" />

## Introductions

-   We’ll be doing group projects and you should form your groups of 2-4 people early in the semester.

-   Let’s take a break to introduce ourselves. Turn on your cameras and say Hi and one or two sentences about yourself and your goals for the course.

# The Steps of an Analysis and R

## Steps of a data analysis

-   Before you start your data analysis and R
    -   Something is happening in the world
    -   Someone collects data
    -   Someone asks a question
-   R Time
    <img src="/img/data-science.png" style="width:75.0%" />

## Tools

-   Many tools exist for these steps:
-   General data tools: R, Python, Julia, Matlab, STATA, SAS
-   Other tools: SQL (data import), git (version control), map/reduce software
    (for big data).
-   Advantages and disadvantages to each.

## R

-   R is a statistical programming (or scripting) language.
-   You write code (a series of functions) to perform some task.
-   R can be used to perform **all** of the tasks of a data analysis.
-   R is built around the idea of *packages*: like apps
    -   Packages are sets of functions designed to work together to accomplish a specific set of tasks
    -   There are thousands of packages and you can install any one with a simple function `install_packages()`

## Motivation for R

1.  It’s free and open source.
    -   You will always have access to R.
    -   Not true for other software (Matlab, STATA, SAS).
2.  It’s widely used with a lot of community support.
    -   If you need some special analysis, someone has often made an R package.

<img src="/img/code_hero.jpg" style="width:50.0%" />

1.  It’s *relatively* easy (especially graphics and data wrangling).
    -   “Evolution” driven by statisticians for local utility more than enterprise software

<img src="/img/r_rollercoaster.png" style="width:75.0%" />

1.  It enables reproducible research and analysis
    -   Copying and pasting across spreadsheets can lead to mistakes - see [](https://www.peri.umass.edu/fileadmin/pdf/working_papers/working_papers_301-350/WP322.pdf) Thomas Herndon, Michael Ash, and Robert Pollin[^4]
    -   In R, you can essentially automate your analysis, reducing the chance for mistakes and making your analysis transparent to the wider research community as well as reproducible.

<img src="/img/reproducibility_court.png" style="width:50.0%" />

## What about Python??

-   Python is also a very good language for data science.
-   As a more general computer language it can be used for developing broader applications.
-   Computer scientists tend to prefer it because its design and syntax is more like a standard computer language.
    -   Can make it harder to learn for a non-programmer.
-   Main reason to use either tool is based on the use case and your collaborators.

## Two main flavors of R Users

-   There are two main flavors of R programmers: Base R users and tidyverse users.

-   Base R is the default system - it’s more general but not as intuitive or consistent as the tidyverse.

-   tidyverse packages are much more convenient for the vast majority of tasks, as long as you drink the Koolaid.

    -   They are not always the fastest but for many many uses and data sets they provide a convenient framework

<img src="/img/tidyverse_celestial.png" style="width:50.0%" />

# This Class - See the Syllabus

## Learning Outcomes

STAT 412/612 will *Develop your competence, creativity, and confidence as a data scientist working with R* so you can …

1.  Execute a regular process to execute reproducible research and analysis using R and R Studio and communicate the results and implications to others.  
2.  Install and use R packages for specific applications
3.  Import data from a variety of external sources
4.  Use tidyverse capabilities to transform data to support analysis in R
5.  Use tidyverse graphical tools to visualize and understand data
6.  Write basic R functions using control and data structures
7.  Employ R functions to conduct statistical analysis and inference
8.  Generate research or analytical reports and presentations using R Markdown and basic LaTeX capabilities.
9.  Deliver an oral presentation describing your data science analysis to an audience .

## Books and Resources:

-   All material used in this course is free and online.
    -   R for Data Science: https://r4ds.had.co.nz/ Garrett Grolemund and Hadley Wickham[^5]
    -   Tidyverse Style Guide: https://style.tidyverse.org/ H Wickham[^6]
    -   RStudio Cheat Sheets: https://www.rstudio.com/resources/cheatsheets/

## References

[^1]: “Data Science: An Action Plan for Expanding the Technical Areas of the Field of Statistics,” *International Statistical Review* 69, no. 1 (2001): 21–26.

[^2]: “Inside Data Science and Its Applications,” *Investopedia* (Investopedia, August 2020), <https://www.investopedia.com/terms/d/data-science.asp>.

[^3]: “Data Scientist: The Sexiest Job of the 21st Century,” *Harvard Business Review* 90, no. 10 (2012): 70–76.

[^4]: “Does High Public Debt Consistently Stifle Economic Growth? A Critique of Reinhart and Rogoff,” *Cambridge Journal of Economics* 38, no. 2 (2014): 257–79.

[^5]: “R for Data Science,” 2018.

[^6]: “The Tidyverse Style Guide,” 2017.
