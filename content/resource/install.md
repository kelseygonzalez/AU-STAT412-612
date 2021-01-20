---
title: Installing R, RStudio, tidyverse, and tinytex
menu:
  resource:
    parent: Guides
type: docs
toc: true
weight: 1
---



You will do all of your work in this class with the open source (and free!) programming language [R](https://cran.r-project.org/). You will use [RStudio](https://www.rstudio.com/) as the main program to access R. Think of R as an engine and RStudio as a car dashboard—R handles all the calculations and the actual statistics, while RStudio provides a nice interface for running R code.


## RStudio on your computer

RStudio.cloud is convenient, but it can be slow and it is not designed to be able to handle larger datasets, more complicated analysis, or fancier graphics. Over the course of the semester, you should wean yourself off of RStudio.cloud and install all these things locally. This is also important if you want to customize fonts, since RStudio.cloud has extremely limited support for fonts other than Helvetica. 

Here's how you install all these things

### Install R

First you need to install R itself (the engine).

1. Go to the CRAN (Collective R Archive Network)^[It's a goofy name, but CRAN is where most R packages—and R itself—lives.] website: <https://cran.r-project.org/>
2. Click on "Download R for `XXX`", where `XXX` is either Mac or Windows:

    <img src="/img/install/install-r-links.png" width="60%" />

    - If you use macOS, scroll down to the first `.pkg` file in the list of files (in this picture, it's `R-4.0.0.pkg`; as of right now, the current version is also 4.0.0) and download it.
    
        <img src="/img/install/install-r-mac.png" width="100%" />
    
    - If you use Windows, click "base" (or click on the bolded "install R for the first time" link) and download it. 
    
        <img src="/img/install/install-r-windows.png" width="100%" />

3. Double click on the downloaded file (check your `Downloads` folder). Click yes through all the prompts to install like any other program.

4. If you use macOS, [download and install XQuartz](https://www.xquartz.org/). You do not need to do this on Windows.


### Install RStudio

Next, you need to install RStudio, the nicer graphical user interface (GUI) for R (the dashboard). Once R and RStudio are both installed, you can ignore R and only use RStudio. RStudio will use R automatically and you won't ever have to interact with it directly.

1. Go to the free download location on RStudio's website: <https://www.rstudio.com/products/rstudio/download/#download>
2. The website should automatically detect your operating system (macOS or Windows) and show a big download button for it:

    <img src="/img/install/install-r-rstudio1.png" width="50%" />
    
    If not, scroll down a little to the large table and choose the version of RStudio that matches your operating system.

    <img src="/img/install/install-r-rstudio2.png" width="100%" />

3. Double click on the downloaded file (again, check your `Downloads` folder). Click yes through all the prompts to install like any other program.

Double click on RStudio to run it (check your applications folder or start menu).


### Install `tidyverse`

R packages are easy to install with RStudio. Select the packages panel, click on "Install," type the name of the package you want to install, and press enter.

<img src="/img/install/install-r-package-panel.png" width="40%" />

This can sometimes be tedious when you're installing lots of packages, though. [The tidyverse](https://www.tidyverse.org/), for instance, consists of dozens of packages (including **ggplot2**) that all work together. Rather than install each individually, you can install a single magical package and get them all at the same time.

Go to the packages panel in RStudio, click on "Install," type "tidyverse", and press enter. You'll see a bunch of output in the RStudio console as all the tidyverse packages are installed.

<img src="/img/install/install-r-tidyverse.png" width="60%" />

Notice also that RStudio will generate a line of code for you and run it: `install.packages("tidyverse")`. You can also just paste and run this instead of using the packages panel.


### Install `tinytex`

When you knit to PDF, R uses a special scientific typesetting program named LaTeX (pronounced "lay-tek" or "lah-tex"; for goofy nerdy reasons, the x is technically the "ch" sound in "Bach", but most people just say it as "k"—saying "layteks" is frowned on for whatever reason).

LaTeX is neat and makes pretty documents, but it's a huge program—[the macOS version, for instance, is nearly 4 GB](https://tug.org/mactex/mactex-download.html)! To make life easier, there's [an R package named **tinytex**](https://yihui.org/tinytex/) that installs a minimal LaTeX program and that automatically deals with differences between macOS and Windows.

Here's how to install **tinytex** so you can knit to pretty PDFs:

1. Use the Packages in panel in RStudio to install **tinytex** like you did above with **tidyverse**. Alternatively, run `install.packages("tinytex")` in the console.
2. Run `tinytex::install_tinytex()` in the console.
3. Wait for a bit while R downloads and installs everything you need.
4. The end! You should now be able to knit to PDF.