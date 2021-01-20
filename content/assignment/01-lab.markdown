---
title: "Lab 1"
date: "2021-01-28"
due_date: "2021-01-29"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Labs
    weight: 1
type: docs
toc: true
editor_options: 
  chunk_output_type: console
---





You'll be doing all your R work in R Markdown this time (and from now on). You should use an RStudio Project to keep your files well organized (either on your computer or on RStudio.cloud). Either create a new project for this exercise only, or make a project for all your work in this class.

## Task 1: Make an RStudio Project

1. Use RStudio on your computer [Follow these instructions if you never got it downloaded](/resource/install/) to create a new RStudio Project.

2. Create a folder named "data" in the project folder you just made.

3. Download this CSV file and place it in that folder:

    - [<i class="fas fa-file-csv"></i> `cars.csv`](/data/cars.csv)

4. In RStudio, go to "File" > "New File…" > "R Markdown…" and click "OK" in the dialog without changing anything.

Your structure should look something like this:
    <img src="/img/assignments/project-structure.png" width="30%" />

## Task 2: Work with R Markdown

5. In the YAML heading (the text between `---`), Write a title, your name, and that you want to output to html

6. After the closing YAML (after the second `---`), Create a level-1 header and then in a new section, introduce yourself. Tell me your name, major, favorite food, and something you did or learning in 2020 to stay sane. Be sure to use _italics_, **bold**, and other[tricks](resource/markdown/).

7. Under a new header, write the DC, Maryland, or Virginia minimum wage, making sure to use the dollar sign. 

6. Save the R Markdown file with some sort of name (**without any spaces!**)


## Task 3: Work with R

1. Add a new markdown header named "R code" and create an R code chunk underneath. Either type <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>i</kbd> on Windows, or <kbd>⌘</kbd> + <kbd>⌥</kbd> + <kbd>i</kbd> on macOS, or use the "Insert Chunk" menu:

    <img src="/img/assignments/insert-chunk-button.png" width="19%" />

2. In the code chunk, load the tidyverse package (remember, `library` or `require`) and load the starwars dataset. 

3. Practice using some of the data exploration commands that were introduced in class. How many can you remember? 

3. Knit your document as an HTML file (or PDF if you're brave and [installed LaTeX](/resource/install/#install-tinytex)). Use the "Knit" menu:

    <img src="/img/assignments/knit-button.png" width="30%" />

4. Upload the knitted document to Canvas. 

5. 🎉 Party! 🎉


{{% div fyi %}}

You'll be doing this same process for all your future labs. Each problem set will involve an R Markdown file. You can either create a new RStudio Project directory for all your work:

<img src="/img/reference/rproj-one-folder.png" width="30%" />

Or you can create individual projects for each assignment and project:

<img src="/img/reference/rproj-multiple-folders.png" width="30%" />

On Canvas, you will turn in your .Rmd, .html, and/or .pdf file. 

{{% /div %}}
