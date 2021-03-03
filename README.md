# Homework: Python Software Carpentry

Tuesdays 2nd & 9th, March 2021 | [Software Carpentry USDA Course Website](https://annajiat.github.io/2021-03-02-usda-online/)


Temporary repo for python software carpentry. Reusable functions will probably be incorporated into other projects and this repository deleted in 30 days.

## Data sets

Example datasets for the homework problems:

```
wget http://swcarpentry.github.io/shell-novice/data/data-shell.zip
wget http://swcarpentry.github.io/python-novice-gapminder/files/python-novice-gapminder-data.zip

ls -1 *.zip
#> data-shell.zip
#> python-novice-gapminder-data.zip

unzip data-shell.zip; unzip python-novice-gapminder-data.zip
```

## General notes on presenting material: 

* Create a `Presenter` account on MacOS or Windows, avoids any errant files and is a clean system for the demonstration
* Explain the ways to ask for help (chat window, DM, interruptions, email)
* Mostly redirecting questions to videos/particular pages in the workshop.
* Questions about checking if software (git/anaconda) is installed properly (windows search in applications/mac magnifying glass)
* Focus on the why "CLI is automated, less error prone than GUI"
* Explain `$` is a prompt (variations in tutorials, enable participants to follow/read tutorials)
* Explain concept, then give an example use case (biological/geospatial/etc), focus on benefits (faster, less errror prone, writing papers).
* edit: Open a standard folder on left, open terminal on right, navigate via `pwd`, `ls`, `cd` in terminal while clicking on folders on left. (Show that gui nav and cli nav is the same)
* Emphasize the hirarchical struture of file directory (example, move into a directory, try to go up one directory level... might just attempt `cd parent` which will give error. Then explain `cd ..`)
* edit: slide with visual? (directory struture, "you are here", arrows for movement with the `cd` command) can be used as a cheatsheet.
* `ls -a -F` explain hidden directory and a `./` for current directory (will be useful for calling commands here "orthogonal")
* Check understanding of "home" multiple choice (chat)
* Filesystem as a hierarchical graph. Ask multiple choice of navigation... okay I like the hierarchical graph questions
* lol, they use my folder naming scheme :) `YYYY-MM-DD`
* Since there are multiple timezones, list breaks in chat "15 min break, restart at XX:15"
* Get list of bash commands (google search a list), can also explain about `ls $PWD` but that might be "too busy" even if it's an exact answer.
* Git Bash has weird "tab-completion" behavior... may need to add `/c/` prefix.
* Windows: `ls /` shows where `git-bash.exe` is installed (not the home directory).  (windows subsystem for linux)... there are always pathing issues on Windows. Best to keep traveling up the parent directory (repeat `cd ..; ls` ) until we find the `C:` system folder. Then navigate down to Desktop and start setting up symbolic links `ln -s`. (hmm wonnder if there's a way to swap sharing for Windows/Mac/Linux... guess this goes into a video comparison).
* Naming conventions with usernames (space and special charactters will wreck havock to any programs installed on Desktop)
* New SCINet users -> pipeline them to the next SCINet Software Carpentry Training (either send the list of emails to coordinator, or give them priority signup for workshops)
* Spend a day without the mouse :) all in commandline ("mouse-less challenge")
* Run the tutorials in breakout rooms. Groups of 4 people work through a tutorial, collectively submit answers to a github repo (foolder named by group). 

## Python

Any dependencies saved into an `environment.yml` file

```
name: jup_env
channels:
  - conda-forge
  - bioconda
  - defaults
dependencies:
  - python=3.8
  - jupyterlab     #<= more recent than jupyter notebooks, more like RStudio?
```
