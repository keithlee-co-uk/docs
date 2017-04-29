# Virtual Environment for the Project
I'm moving away from virtualenv, which I have used extensively with my Python2 projects.

An interesting discussion about Virtual Environments may be found at [Virtualenv's bin/activate is Doing It Wrong](https://gist.github.com/datagrok/2199506)

Briefly, for Python versions 3.4 & 3.5, the recommended virtual environment method was by using the [pyvenv](https://docs.python.org/3/library/venv.html),  but for Python3.6 The pyvenv script has now been deprecated in favour of using
`python3 -m venv`


I'm assuming the use of the [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) shell, though alternatives are available.

----

* **[Index Page](README.md)**

* reference: [venv](https://docs.python.org/3/tutorial/venv.html)

----

## Table of Contents

* [Python Versions](#Python-Versions)
* [Python version, for the Environment](#Python-version,-for-the-Environment)
* [Virtual Environment for the Project](#Virtual-Environment-for-the-Project)




----


## Python Versions

`pyenv install <python version you require for your project>`

for example
`pyenv install 3.6.0`

`cd <path to repo>/<project name>`  
`pvenv local 3.6.0`

#### Exclude the Python Version file from git

`echo ".python-version" >> <path to repo>/<project name>/.gitignore`

----
## Project Environment Naming Conventions
When you *activate* a Virtual Environment the prompt is altered to the name of the environment.

It is possible to have multiple environments for each project, this is useful for testing with the likes of [tox](http://tox.readthedocs.io/en/stable/) *TBC* and to have open more than on project at a time in various terminals or just not recall if you activate one environment or another, just before you got that phone call.

I suspect that this could become confusing if the name of the environment is the same across various projects.

This is the naming convention that I intent to follow.

`<path to repo>/<project name>.env/<project name>-<python version>`

where <python version> is in the form of py34 for Python3.4, py36 for Python3.6 etc.

## Create the Virtual Environment

Creating a project called *MyProject* with a virtual environment that will run with Python3.6

`python -mvenv <path to repo>/MyProject/.env/MyProject-py36`

To change the python version you wish to use for your virtual environment, before creating a new environment.

for example using Python3.5  
*(this assumes that you already installed the version you want to use [Python version, for the Environment Project](#Python-version,-for-the-Environment-Project))*

`pyenv local 3.5.0`

`python -mvenv .env/MyProject-py35`

## Exclude the Environments from git

`echo ".env/*" >> <path to repo>/<project name>/.gitignore`

## Activate the Environment

Note that this currently is *"Wrong"* as described in [Virtualenv's bin/activate is Doing It Wrong](https://gist.github.com/datagrok/2199506)

`source <your project path>/.env/MyProject-py36/bin/activate`  
or  
`source <your project path>/.env/MyProject-py35/bin/activate`  

----
----

* [Development Machine Install](DevelopmentMachineInstall.md)
* **[Index Page](README.md)**



