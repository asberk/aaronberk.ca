+++
date = "2020-04-14T12:00:00"
draft = false
tags = ["python", "software", "install"]
title = "Python installation tutorial"
summary = "Install python3 using Homebrew."

[header]
image = ""
caption = "Image credit: []()"

+++


There will be approximately three steps to this tutorial.

1. Install Homebrew
2. Use `brew` to install the latest version of `python`  
 Verify that the installation is working correctly and troubleshoot if
 necessary.
4. Install useful packages using `pip`.  
 Ensure they are working and troubleshoot if necessary.


## Installing Homebrew

A main tool in our installation process will be homebrew. Homebrew is a package
manager for Mac OS that is extremely handy, well beyond the scope of installing
Python. First we'll check if homebrew is already installed. To do so, run the
following snippet and look examine the output. If homebrew is installed, then it
should print out some version information.

    > brew --version
    Homebrew 2.2.12
    Homebrew/homebrew-core (git revision d51e0f; last commit 2020-04-09)
    Homebrew/homebrew-cask (git revision 78b7f; last commit 2020-04-09)


If running the above command gives an error because `brew` is not a defined
command, then you'll have to install homebrew. To do so, open a new Terminal
window and enter the following (this snippet was taken from the [homebrew main
page](https://brew.sh/)).

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

As a brief caveat, it's possible you will first have to install some XCode
components required by `brew`, in which case `brew` should let you know. Be
prepared to run the following snippet and follow along with the install
instructions.

```bash
xcode-select --install
```

If the installation of brew worked, then you should now be able to run 
```bash
brew --version
```
and see some version information as per the above.

## Installing Python

Now, installing Python should be as easy as running:

```bash
> brew install python3
<<long>>

> python --version
Python 3.6.10 :: Anaconda, Inc.

> pip -V
pip 20.0.2 from /Users/aberk/anaconda/envs/py37/lib/python3.6/site-packages/pip (python 3.6)
```

**Note:** An alternative to the homebrew installation avenue is to download an
installer file from the [official Python
page](https://www.python.org/downloads/release/python-382/). I have no
familiarity using this avenue.

## Installing commonly used packages

This tutorial was tailored for a machine learning audience, so the installed
packages will contain some packages that are useful for ML.

```bash
> pip install numpy pandas matplotlib 
> pip install scipy seaborn sckit-learn
> pip install feather-format
> pip install torch torchvision
> pip install notebook jupyterlab
```

There are numerous other useful packages to install, but let's see if we can get
up and running with these first. In all cases, you should be able to confirm
that a package was installed correctly by running the following snippet and
observing the package's version number as the output.

```bash
> python -c 'import the_package; print(the_package.__version__)'
```

For example, on my machine:
```bash
> python -c 'import numpy; print(numpy.__version__)'
1.18.1
```

In rare instances, a package may not implement the (more-or-less standard)
`.__version__` syntax. Python will throw an error in this exceptional case.

## More information

See
[here](https://medium.com/faun/the-right-way-to-set-up-python-on-your-mac-e923ffe8cf8e)
for some alternative information on installing Python and managing
environments. The post seems slightly out-of-date (by about a year). The short
timeframe of this obsolescence does not bode well for the present tutorial. :sweat_smile:

For learning how to program in Python, the [official
documentation](https://docs.python.org/3/tutorial/) provides extensive resources
for getting up-and-running, as well as a [language
reference](https://docs.python.org/3/reference/) which serves as a bit of a
dictionary once you're mostly up-and-running. Another great tutorial resource is
[Patrick Walls's UBCS3 page](https://www.math.ubc.ca/~pwalls/#ubcs3) which
includes some "[mathematical
Python](https://www.math.ubc.ca/~pwalls/math-python/)" walkthroughs, and
"machine learning with Python" walkthroughs.

## Intro to PyTorch

The purpose for this post was to establish the environment for an [Intro to
PyTorch](https://github.com/asberk/intro_pytorch) tutorial. Follow the link for
the repo.
