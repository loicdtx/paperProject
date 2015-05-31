## Project structure for paper projects

*I spent a lot of time trying to find the optimal way to organize my projects, and I found something that works (at least it works for me), so I thought I'd share it. Feel free to ask questions, use the structure for your own projects, and suggest improvements*

### What is that ?

This repository details the project structure I follow for paper projects. When working on a scientific publication, it is easy to become overwhelmed by the complexity and diversity of the project itself. This may result in large amounts of overhead, looking for the script that produces a certain figure or trying to figure out which version of the manuscript is the most up to date. With a good structure from the initiation of the project, this overhead can be reduced and time can be spent on doing actual work, rather than figuring out which file does what. Re-opening a project after 3 months when reviewers comments arrive is then much easier.r.

### Exploring this repository

Each directory in this project contains a README.md file explaining the function and the logic of that project section. They can be visualized directly in github by navigating through the project folders.

### Root of the project (This directory)

This directory, which we will name *project root* contains four important files.
- A git project file (`.git`): *Not visible, hiden file*
- A `.gitignore`
- A `projectName.Rproj` file: Configuration file for RStudio IDE
- A `.Rprofile` file

#### Content of the `.gitignore`

The `.gitignore` file lists the files that should be ignored by the version control system. My `.gitignore` has the following content.

```
.Rproj.user
.Rhistory
.RData
/latex/*
*~
!/latex/*.tex
!/latex/*.bib
!/latex/figs/
```

The reason for the `/latex/*` entry in the `.gitignore` is that latex generates a lot of temporary files which you absolutely do not want to commit to git. The rule is to only commit files on which you make changes and not commit any automatically generated file, and that includes the pdf of the manuscript. When you really want to add a file to the git index, it's possible, simply try to do it; it's not going to work but git will nicely tell you how to do it.

#### Content of the `projectName.Rproj` file

`.Rproj` files are the default configuration files for RStudio. Most of the content will be generated automatically when initializing a RStudio project, and this does not need to be edited (unless you want to).

By default the `.Rproj` file will contain the following content (more or less, depending on your global settings):

```
Version: 1.0

RestoreWorkspace: Default
SaveWorkspace: Default
AlwaysSaveHistory: Default

EnableCodeIndexing: Yes
UseSpacesForTab: Yes
NumSpacesForTab: 2
Encoding: UTF-8

RnwWeave: Sweave
LaTeX: pdfLaTeX
```

#### Content of the `.Rprofile` file

The `.Rprofile` file is a file that gets sourced on RStudio startup, so it is conveinient for setting variables that you use all the time. For example, I use several machines, so that my data is in a different path depending on the machine I am using. The following code sets the path according to my machine name. I could paste this code snippet in the header of every script, but I'd rather have it in my `.Rprofile`. When I start my RStudio project the `path` variable is already set.

```r
# Set path for all machines
if(.Platform$OS.type == 'windows') {
    path <- 'F:/RS'
} else {
    info <- Sys.info()
    if (info['nodename'] == 'vanoise') {
        path <- '/media/dutri001/LP_DUTRIEUX_Data/RS'
    } else if (info['nodename'] == 'papaya') {
        path <- '/media/DATA3/dutri001'
    } else if (info['nodename'] == 'tanargue') {
    	path <- 'media/whatever/'
    }
    
} # For some reasons the empty line at the bottom is important

```


> Note: When working outside of RStudio, running a script with the `RScript` command for example, the `.Rprofile` file may not be sourced, so you'll need to set these variables in the header of the script. (TODO: need to check that)

