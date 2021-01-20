---
title: "Overview"
date: "2021-01-19"
due_date: "2021-04-19"
due_time: "11:59 PM"
menu:
  assignment:
    parent: Final Project
    weight: 1
type: docs
toc: true
editor_options: 
  chunk_output_type: console
---


# Learning Outcomes

The final project is a group analysis of a real-world situation using the tools from this course to produce a written report and presentation. Your group will also submit a progress report.  

The learning outcomes include:  

- Work as part of a diverse data science group to solve a complex problem
- Interpret project requirements and organize the project to provide high-quality, compliant deliverables
- Identify data sources of interest
- Conduct a literature review to shape the context for the analysis
- Use tidyverse capabilities to 
  + Collect, clean, tidy, organize raw data sets
  + Conduct Exploratory Data Analysis using numerical and Graphical methods
  + Manipulate data to support analytical requirements
- Use Data Science tools and methods to:
  + Produce transparent and reproducible analysis to address questions of interest
  + Identify questions of interest and initial hypotheses, analyze the data, and update the hypotheses based on correct interpretation of the analysis
  + Develop findings and recommendations
  + Organize your analysis to support communication of your work and results
- Use R Markdown capabilities to:
  + Create a high-quality, formatted report
  + Create a high-quality, presentation 
- Communicate your results in a concise, and compelling manner
  + Synthesize your work into a concise Executive Summary (Abstract)
  + Deliver a group/individual presentation on the analysis
  + Deliver a group report that effectively captures the essence of the work in the main body with supporting appendices
  

# General Requirements

For the final project you will work in groups of 2 to 4 people to complete this assignment *using tools from the class.*

- Students enrolled in 412 will provide results based on data cleaning, visualization, and data analysis. 
- Students in 612 will provide results based on data cleaning, visualization, data analysis, and *statistical analysis/inference.*  

Work with me to get your topic and dataset approved. Your project should involve working with a fairly large, real-world dataset from a primary source to answer questions on a topic of interest to the group. The analysis should be reproducible. 
You may only discuss your project with your own group members (and me, of course). You may not discuss your project with the members of other groups or people outside of the class.

There are four deliverables: 

1. Progress Report
2. Final Report
3. Presentation Document - Slides
4. Oral Presentation - Delivered by each group member

The progress report will be submitted on Canvas in .Rmd and PDF formats.  

The Final Report and Presentation Document must be submitted on Canvas as part of a single .zip file containing the entire Final Project effort. 

- The .zip folder should contain everything necessary to run the analysis and recreate the final project report and presentation document (using relative paths).
- The top level folder should use the project name. It should also have an analysis folder (containing the .Rmd and PDF files for both the final report and presentation document) and a data folder with all the data uploaded for analysis. 
- The .zip file should include, only as necessary, a data_raw folder, a graphics folder, and/or an output folder.
- The zip should not include any extraneous files or output. 
- I should be able to run and reproduce your documents after unzipping the project folder.

Specific requirements for each deliverable are in the sections below.
There are three appendices that may help in structuring your documents, understanding the peer evaluation rubric, and investigating possible topics and data sources

## Important Dates

- **02/28/2021**: Each student submits the names of their group members and the general topic.

- **03/14/2021**: Each group submits a two-page Progress Report in .Rmd and PDF format. 

- **04/19/2021**: Each group submits a zipped folder to Canvas containing all of your analyses, scripts, and inputs/data in the appropriate directory structure. I should be able to run everything after unzipping the project folder.

- **04/19 & 04/22/2021**: Each group delivers an oral presentation using the group's presentation document 

# Appendices
## Appendix 1: R Markdown Code Chunk Options to Control Display of Code and Chunk Output
- One of the beauties of R Markdown is you can use Code Chunk options to determine which portions of your analysis get included in a report. For more info see:  [knittr](https://yihui.org/knitr/options/#:~:text=The%20knitr%20package%20provides%20a,to%20customize%20the%20knitting%20process.)
- Options go after the r, in the `{r} separated by a comma and space,
  + e.g., `{r, echo = FALSE, eval = TRUE, include = FALSE}`

### Four options of interest 
  + `echo = ` determines if the code will be shown in the output. 
    - If FALSE, no code will be shown
  + `eval = ` determines if the code will be evaluated (run) during the production of the output.
    - If FALSE, the chunk will not be run during the knit process so no output will be displayed and it will not be available for later code chunks
  + `include = `determines whether to include the chunk *output* in the output document. 
      - If FALSE, no output from the chunk will be written into the output document, but the code is still evaluated (assuming `eval = TRUE`)
      - Plot files are generated if there are any plots in the chunk, so you can manually insert figures later
  + `message = `: whether to preserve messages. 
    - If FALSE, any messages from the code will not show in the output.

### Examples
1. You don't want to show the code or run it for producing the final document. Use `{r, echo = FALSE, eval = FALSE}
2. You don't want to show the code but you want to show the code output in the final document. Use `{r, echo = FALSE, eval = TRUE}` 
3. You don't want to show the code but you need to run it to use the results later in the analysis but you don't want to show the code output in the final document. Use`{r, echo = FALSE, eval = TRUE, include = FALSE}

### Structuring Your Code Chunks
- You can use these tags for R Markdown files producing normal documents or presentations
- Using them can save you a lot of cutting and pasting which can creating logic errors
- They also mean you should shape your code chunks to split actions into multiple pieces. 
- That allows you to do your analysis in a logical sequence but not show the initial pieces and then show the final plot or numerical summary.


## Appendix 2: Presentation Assessment Form - Peers 

Your Name______________________

### Presentation Group 1: Subject __________________________________

1. Was the Presentation professional?  Major Gaps\hspace{.25in}Minor Gaps\hspace{.25in}Very Nice\hspace{.25in}Great!

    - Clean Slide layout
    - Slide content easy to understand
    - Presenters told a story (not just read the slides)
    
2. Was the Presentation Convincing?  Major Gaps\hspace{.25in}Minor Gaps\hspace{.25in}Very Nice\hspace{.25in}Great!
    - Situation Clear
    - Analysis Approach was appropriate
    - Findings supportable
    - Recommendations relevant
    
Comments: 



## Appendix 3: Data Sources

Here are some possible sources for data. I will not accept small curated datasets, or those that come from a paper where the data has already been analyzed.

I will accept other sources as long as they are comparably large and complicated. For example, there are many open data portals from the federal governments, states and cities., e.g. (https://ohio.gov/wps/portal/gov/site/government/resources/ohio-data-analytics).

- Data quest Blog has pointers to many data sets

  <https://www.dataquest.io/blog/free-datasets-for-projects/.>

- Federal bridge inspections from the Federal Highway Admin: 

    <https://www.fhwa.dot.gov/bridge/nbi/ascii.cfm>
    
- Drinking water violations from the EPA: 

    <https://www.epa.gov/ground-water-and-drinking-water/drinking-water-data-and-reports>

- Contracts or grants from USA Spending: 

    <https://www.usaspending.gov/#/>

- DC Crime incident data from the DC police: 

    <https://mpdc.dc.gov/page/statistics-and-data>

- SBA disaster loans from the Small Business Administration: 

    <https://www.sba.gov/offices/headquarters/oda/resources/1407821>

- Fatal accidents from the NHTSA: 

    <https://www.nhtsa.gov/research-data/fatality-analysis-reporting-system-fars>

- Baltimore crime data from the Baltimore police: 

    <https://www.baltimorepolice.org/crime-stats/open-data>

- Aircraft animal strikes from the FAA: 

    <https://wildlife.faa.gov/databaseSearch.aspx>

- Bank health data from the FDIC (also see banktracker at IRW): 

    <https://www.fdic.gov/bank/statistical/guide/data.html>

- USGS water quality data from the USGS: 

    <https://water.usgs.gov/owq/data.html>

- Prison data: 

    <http://www.dc.state.fl.us/pub/obis_request.html>
    
- College Scorecard: 

    <https://catalog.data.gov/dataset/college-scorecard>
    
- Reporting Carrier On-Time Performance (1987-present) from the Bureau of 
  Transportation Statistics:

    <https://www.transtats.bts.gov/DL_SelectFields.asp?Table_ID=236>
    
- The General Social Survey from the non-partisan and objective research organization at the University of Chicago (NORC):

    <https://gssdataexplorer.norc.org/>
