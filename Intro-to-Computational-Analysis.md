---
title: "Intro to Computational Analysis"
author: "Emilie Théberge"
output: 
  html_document:
    keep_md: yes
    toc: true
    toc_float: true
    toc_collapsed: true
    number_sections: true
    theme: lumen
---



**Version 4.0 (June. 2021)**

Thank you for the feedback Paola, Will, Victor, Amy, Almas and Nikita from the Dennis and Robinson labs for feedback throughout versions 1 and 2 (July 2020).

*These chapters assume no prior computer science/coding course experience.*

# Introduction

Code is a language. A basic understanding of common vocabulary and programming concepts is essential to be able to follow and customize code shared by other users to use in your own analyses; nefore being able to work with data and apply tools using the R or Python languages in RStudio or the command line (ie. via Terminal/Sockeye), you need to learn the language's "alphabet" - imagine you're a native English speaker learning Russian, Greek or Korean for the first time. How can you read without knowing the alphabet? Right. 

Without this essential foundation, annotations and explanations of specific code created by users for other users might look and sound like gibberish. This document is to help you get a "lay of the land" and learn that alphabet and key vocabulary.
 
Back to learning code: When self-teaching or following a course, it's important to be able to recognize what level you're at, and if the material is the right level for your understanding at that moment. If you jump into searching for and applying complex code from other authors too soon, without understanding the basics, you may overwhelm yourself and be lost. Metaphorically, this is like a Russian teacher asking you to compose your own sentences and essays with the new language before you’ve finished learning the Russian alphabet and basic grammar tenets. This would be like copy/pasting from previously written essays, and just hoping that there’s some sort of logical flow achieved and no grammar errors come up. (This is a metaphor for when your code doesn’t work and you don’t know why.)
 
If something goes wrong within your editing of someone else’s code to fit your own data, it’s vital to understand the basics of this analogous coding “alphabet” and “grammar” to fall back on when troubleshooting, and know the best online resources available for where to look for help. Learning the details of specific packages is not what will be covered in this document; this document will contextualize learning what a package is, and other basic statements when learning and applying programming languages.  
 
Each language and environment has its own host of materials on the internet to get you familiar with more details. Many free courses and walkthroughs with different iterations of “Intro to _(package name)_ in (R/bash)” are available, which are in another folder in this github repository. Speaking from personal experience, I would recommend looking at these more specific tutorials (eg. TOG workshops to apply specific packages in R) *after* learning some programming basics as introduced in this document.
 
The aim is for you to have these programming basics contextualized before putting these languages and environments into more specific use through the different avenues your graduate thesis project process may take. 
 
# Coding languages and environments

**R & RStudio** 

* Download from the internet 
* RStudio is the ‘house in which things are done’ which requires R to be downloaded first as the ‘scaffolding/foundation’ 
* R is responsible for importing data, manipulating data, graphics, etc. 
* Rstudio is an IDE (integrated development environment) that makes it “easier” to work in R (more user-friendly) and lets you run code directly from .R, .Rmd, and other files. You can import data sets (such as in .csv) and manipulate/do various statistical analyses & graphical representations 
* R language has some “universal” vocabulary/grammar but, as every package is designed by different individuals, the wording, details and utilities of functions vary across each package. 
* See RMarkdown files (.rmd) for explanations of utilities of different packages written and annotated by the users (and collaborators) to be followed along and replicated by other researchers. 
  * https://www.r-project.org/ 
  * https://rmarkdown.rstudio.com/articles_intro.html 

**Python & Jupyter Notebook** 

* Download from the internet     
* Python is to R as Jupyter is (somewhat) to RStudio      
* Jupyter Notebook is a web-based interactive computing platform       

* Biology Meets Programming: Bioinformatics for Beginners (Python in biological context):  https://www.coursera.org/learn/bioinformatics#syllabus 
  * https://www.python.org/downloads/ 
  * https://jupyter.org/ 
 
**Command line & Terminal**

* Already exists on your computer (Windows, Mac, etc.) 
* “Coding in the command line” is synonymous with opening the Terminal application from your utilities folder (on a Mac) and just typing in code there to execute whatever scripts you want to run 
* Python and R are both languages that can be run on the command line 
  * Basic Terminal Usage Cheat Sheet: https://www.youtube.com/watch?v=jDINUSK7rXE 

**BashShell & Linux**

* Linux is an operating system. Windows, macOS, iOS are other examples of operating systems. 
* Linux, unlike other operating systems, is open source software. It’s free and available to the public to view, edit, and contribute to. 
* You probably already use Linux, whether you know it or not (webpages, apps, etc.) 
* Bash is the default “user shell” (=Unix shell) on most Linux installations. It’s a command language for talking with interfaces like Sockeye. 
 
**Sockeye**

* Is UBC's high performance computing (HPC) system interface 
* Is a fancier version of Terminal - talking to the computers at UBC 
* Use Linux/Sockeye for high-computational datasets (ie. SNP or methylation array data) 
* Know how much RAM your computer has; PLINK is an example of a program that may say you’ve run out of memory on your local computer such that you need to use a computational cluster, like Sockeye (https://arc.ubc.ca/ubc-arc-sockeye) 
 
**Git & Github**

* Git is installed on your local system as a “version control system”. It isn’t a coding environment, but keeps track of your coding history. 
* Github is a web platform: an open-source cloud repository to share code 
* The common use for researchers is through sharing Rmarkdown/Rscripts for sharing within and between project groups 
  * Git vs. Github: What’s the difference?: https://blog.devmountain.com/git-vs-github-whats-the-difference/ 
  * “Happy Git and GitHub for the useR” (from STAT 545): https://happygitwithr.com/ 
 

# Workflow of conducting analyses of biological data 

For all types of -omics analyses, as well as integrating non-omics variables (eg. clinical values from EHR data), the general workflow goes like: 
 
1. Import raw data from the source 
* eg. SNP microarray data tech, GWAS summary statistics from the internet, dbgap data, EHR data as .csv, etc.

2. Process in command line (This is an intermediate step not necessarily required for all data - more important for larger/more complex data sets) 
* Terminal, Sockeye, etc, use specific programs designed for manipulating that data 
  * eg. MAGMA, LIMMA, PLINK (1.9) for genotype data 

3. 	Perform statistical analyses and data visualizations 
* Most commonly done in RStudio through packages specific to the type of analysis being performed, eg. through ggplot2/diplyr packages 
* Also can be done through Python code in Terminal, eg. PLINK 
* “Combining” of multiple data sets done at this step, eg. SNP data with methylation for a given set of samples; example of how to do this done in a previous TOG workshop (see other folder in this repository for TOG info) 
 

# Overview of key programming concepts and vocabulary 

**Package:** A collection of functions and data sets developed by the community. 

* These have to be installed manually/individually through the R console using install.packages() function. 

**Library:** A collection of packages. Offers a set of functionalities without worrying about subsequent packages. A library is what you include when you want to add some functionality to your code. Very similar in definition to a repository (which is a more private kind of library).  

* After having installed a package in R (see above ^), use `library()` to load packages in R so they’re “active” and ready to be used in your console (where the coding is done). Packages are installed in your console’s “library”. 
  
**Function:** A block of code that can be referenced by name to run the scripts (code) it contains. 
 
**Scripts:** A series of scripts, or set of steps, are written for a computer to follow. Computers process the steps line-by-line from top to bottom. Each step is created by writing a statement. Scripts can contain multiple functions and variables. 
 
**Variable:** Don’t mix this up with the definition of biological variables (dependent/independent)!! A variable, once declared in code, stores data - they can contain a singular data element (qualitative “character” or quantitative “numeric” or boolean true/false “logical”), or entire data sets (“data frames”). Most variables are vectors. 
 
Scripts, variables and functions look different in Python script (executed in Terminal). 

Something to be aware of and keep in mind as you learn these languages are where there are similarities and differences in where and how each language is applied. 
  
Imported data can be described as either a... 
 
**Data frame:** A data frame contains a collection of “things” (rows) each with a set of properties (columns) of different types. In a data frame, the columns can contain different types of data (ie. column A can have qualitative values, column B can have quantitative, etc.) 
 
**Matrix:** A matrix, in R, is when all of the elements in the data frame contain the same type of data (usually numbers). Matrices are more efficient with memory and applying computations than data frames.
 
More programming definitions:

**Program:** A collection of instructions written in a programming language that performs a specific task when executed by a computer. 
* R and Python are programming languages.
 
**Computing/Network Servers:**  Computing servers are the “foundation” hardware that provides functionality for other programs or devices. UBC maintains various network servers from which you can connect to from your personal computer. To connect to some pages within UBC research facilities, such as the finance page of your student hub, you need to connect first to a secure VPN (virtual private network) through your CWL to get connected to the UBC network server. Another example utility is that you need to be connected to the UBC computing server to use the UBC ARC’s Sockeye platform for huge datasets.
 
**Shells:** A shell is a command line interface (ie. Terminal, Sockeye) to an operating system (ie. Windows/MacOS, Linux, respectively).
 
**Nodes:** A node is a device (ie. personal computer) within a network of other tools that’s able to send, receive, or forward information. Nodes also include devices that connect over Wi-Fi or Ethernet, such as modems, servers and printers. A node may also describe a computer file in a tree data structure; these files are called “leaves” or “leaf nodes”.

**Software:** A collection of data instructions that tells the computer how to work. There’s application software (eg. on a Mac: iTunes and Photo Booth) and system software (eg. MacOS, Linux).
