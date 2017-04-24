# Installing other versions of Python on Debian 8 (Jessie) for Development using pyenv

----
## Links
[Pyramid Development with Docker](Pyramid Development with Docker.md)

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
  eval "$(pyenv virtualenv-init -)"
fi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


eval "$(pyenv init -)" is need to place the various versions of Python you may wish to have in

eval "$(pyenv virtualenv-init -)" enables the plugin that allows you to create virtualenv environments for your specific project


## About usage

It's worth studying [pyenv README.md](https://github.com/pyenv/pyenv/blob/master/README.md) to aid understanding and the usage of pyenv

To install the version of python you require into pyenv

  `pyenv install 3.6.0`

----

*author: Keith Lee <code@keithlee.co.uk>*

*last updated: 2017-04-20 21:40:03*


