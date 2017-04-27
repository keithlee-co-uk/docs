# Installing other versions of Python on Debian 8 (Jessie) for Development using pyenv

**pyenv** enables you to install multiple versions of Python without messing up the base install for your OS

It is *NOT* a virtual environment (as I thought to begin with), though pyenv-virtualenv, a plugin for pyenv for handling virtualenv, with help you with this.

There is also [pyvenv](https://docs.python.org/3/library/venv.html), which comes with Python3.4 but for python3.6 The pyvenv script has been deprecated in favour of python3 -m venv.

This is why I have decided to jump from Python2.7.n, in which I was using virtualenv, to Python3.6 to reduce the amount of learning required to understand the foibles of each system.
 
----

* [Index](README.md)

----

The following is derived from and answer by [Nick T](https://askubuntu.com/users/140640/nick-t)
to the question [How do I Install Python3.6 using apt-get](https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get) on [ask ubuntu](https://askubuntu.com/)

I've carried out this using a base [netinst](https://www.debian.org/releases/stable/debian-installer/) of [Debian](https://www.debian.org/) 8.5 (Jessie)

----


## Table of Contents

* **[Dependencies](#Dependencies)**
  * [Other things you may wish to install](#other-things-you-may-wish-to-install)
  * [Installing the Dependencies](#installing-the-dependances)

* **[Installing pyenv](#installing-pyenv)**
  * [Ensuring pyenv works for you](#ensuring-pyenv-works-for-you)

* **[About usage](#about-usage)**


----

## Dependencies

The versions show are those that worked for me at the time of writing and were the defaults at the time unless otherwise stated.

* curl (7.38.0) - enable downloading of the pyenv installer
* git-all - required for the install of the pyenv installer
* build-essential (11.7) - required for compilation
* zlib1g-dev (1:1.2.8.dfsg-2+b1) - required for the install of Python 3.6.0 using pyenv
* libbz2-dev (1.0.6-7+b3) - required for the install of Python 3.6.0 using pyenv
* libssl-dev (1.0.1t-1+deb8u6) - required for the install of Python 3.6.0 using pyenv
* libreadline-dev (6.3-8+b3) - required for the install of Python 3.6.0 using pyenv

### Other things you may wish to install

* vim-nox - I installed this to aid using vim to edit the .profile file (I tend to forget the key combos and use the arrow keys, the nox version has some nice features I like to use too)


Also suggested by [Nick T](https://askubuntu.com/users/140640/nick-t) were, but my install seemed to not be relevant for the install of Python 3.6
* libsqlite3-dev (3.8.7.1-1+deb8u2) - a warning is issued if this is not installed but it is not required for the
* tk-dev


### Installing the Dependencies

  `sudo apt-get install curl zlib1g-dev build-essential libbz2-dev libssl-dev libreadline-dev git-all vim-nox`


## Installing pyenv

run the following from the command line

  `curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer|bash`


That should be it all installed just reboot or restart the terminal if you are using a graphical shell, such as Gnome to pick up the addition to the .profile file and enable pyenv.


### Ensuring pyenv works for you

I added the following to the end of ~/.profile

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
if [ -d "$HOME/.pyenv" ] ; then
  export PYENV_ROOT="$HOME/.pyenv"
  export PATH="$PYENV_ROOT/bin:$PATH"
  eval "$(pyenv init -)"
fi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


eval "$(pyenv init -)" is need to place the various versions of Python you may wish to have in


## About usage

It's worth studying [pyenv README.md](https://github.com/pyenv/pyenv/blob/master/README.md) to aid understanding and the usage of pyenv

To install the version of python you require into pyenv within the directory you wish this version of python to work with.
If the requested version is not currently part of pyenv then it will be installed and a .version.py file will be placed in the directory you are in so that the pyenv *shim* will take effect down the directory tree.

  `pyenv install 3.6.0`

----

* [Index](README.md)

----

*author: Keith Lee <code@keithlee.co.uk>*

*last updated: 2017-04-27*




