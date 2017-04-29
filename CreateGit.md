# Create a Git Repository for the Project
---


* **[Index Page](README.md)**

----

## Table of Contents

* [Project Directory](#Project-Directory)
* [Virtual Environment for the Project](CreateVENV.md)
* [Python versions](Python version, for the Environment)




----
## One off Git Tasks
These tasks need only be performed once for a new development machine. They set the name and email address you will use for all your project commits from this development machine.


`git config --global user.name <name>`

`git config --global user.email <email>`


There are many options and settings for [git](https://git-scm.com/), these values may also be set on a project by project basis too. There are several [tutorials](https://git-scm.com/docs/gittutorial) and [guides](http://rogerdudler.github.io/git-guide/). It's well worth reading a few.


----
# For each Project

`git init <path to repo>/<project name>`

`cd <path to repo>/<project name>`

`git remote add <name> <url>`

<url> will depend on where you have your remote Repository.


`touch README.md`

`git add README.md`

`git add commit -m "Initial Commit"`

`git push -u origin master`


----

* **[Index Page](README.md)**



