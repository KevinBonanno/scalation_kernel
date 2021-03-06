# Installation Guide

## Table of Contents

<!-- toc -->

- [General Instructions](#general-instructions)
- [Quick Setup Scripts](#quick-setup-scripts)
  * [Quick Setup using Git](#quick-setup-using-git)
  * [Quick Setup without Git](#quick-setup-without-git)
- [Docker Container](#docker-container)
- [Development Version](#development-version)
  * [Install ScalaTion Kernel from GitHub using PIP](#install-scalation-kernel-from-github-using-pip)

<!-- tocstop -->

## General Instructions

Installation requires a recent ScalaTion distribution (>= 1.3) from
[here](http://cobweb.cs.uga.edu/~jam/scalation.html). Once you have
ScalaTion, make sure the ``SCALATION_JARS`` environment variable is
set appropriately before continuing. This can be done individually,
as seen here:

```
$ export SCALATION_JARS=/path/to/scalation_mathstat.jar
$ export SCALATION_JARS=/path/to/scalation_modeling.jar:$SCALATION_JARS
```

It can also be done with a single command if you know the path to the
``scalation_models`` directory:

```
$ export SCALATION_JARS=$(find /path/to/scalation_models/lib | grep .jar | paste -sd ":" -)
```

If you plan on using the kernel in a
[JupyterHub](https://jupyterhub.readthedocs.io/en/latest/) environment, then
you must configure it to recognize the `SCALATION_JARS` environment variable
by adjusting the `c.Spawner.env_keep` or `c.Spawner.environment` options in
`jupyterhub_config.py` appropriately. 

To install **Scalation Kernel** from PyPI, you can use the following
commands:

```
$ python3 -m pip install -U scalation_kernel
$ python3 -m scalation_kernel.install
```

After installing ScalaTion Kernel, you may want to test it out
with Jupyter. To run Jupyter, you might use the following command:

```
$ python3 -m jupyter notebook
```

## Quick Setup Scripts

**Use Case:** The user wants to rapidly deploy a local Jupyter instance with 
ScalaTion notebook support.

A quick setup script is provided that creates an independent Python 3 virtual 
environment using [`virtualenv`](https://virtualenv.pypa.io/en/stable/) and 
installs everything you need to get started with Jupyter, ScalaTion Kernel,
and ScalaTion 1.4. To inspect this script before you run it, see
[`quick_setup_1.4.sh`](quick_setup_1.4.sh). To download and run the script, you
have two options, outlined below, depending on whether or not you have Git 
installed. These instructions assume you are using one of Linux, MacOS, or 
Windows 10 (with 
[Windows Subsystem for Linux](https://msdn.microsoft.com/en-us/commandline/wsl/about)).

### Quick Setup using Git

Open your terminal and run the following commands to setup and run everything
in a Python 3 virtual environment under a subdirectory called `venv-dir` (which
the script will create, if needed):

```
$ git clone https://github.com/scalation/scalation_kernel.git
$ cd scalation_kernel
$ bash quick_setup_1.4.sh venv-dir
```

The first time the script runs, it may take some time due to downloading
dependencies. Subsequent runs should launch Jupyter rather quickly.

### Quick Setup without Git

If you don't have Git installed, download the 
[`zip`](https://github.com/scalation/scalation_kernel/archive/master.zip) or
[`tar.gz`](https://github.com/scalation/scalation_kernel/archive/master.tar.gz)
file and extract it. By default, the directory should be named 
`scalation_kernel-master`. Open your terminal, change into the extracted
directory, and run the following commands to setup and run everything
in a Python 3 virtual environment under a subdirectory called `venv-dir` (which
the script will create, if needed):

```
$ bash quick_setup_1.4.sh venv-dir
```

The first time the script runs, it may take some time due to downloading
dependencies. Subsequent runs should launch Jupyter rather quickly.

## Docker Container

A [`Dockerfile`](https://github.com/scalation/scalation_kernel/blob/master/docker/Dockerfile) 
is availble to those with [Docker](https://www.docker.com) installed.
Instructions on how to build and run the Docker image using the provided `Dockerfile` can be 
found [here](https://github.com/scalation/scalation_kernel/tree/master/docker).

## Development Version

### Install ScalaTion Kernel from GitHub using PIP

The development version of ScalaTion Kernel is hosted 
[here](https://github.com/scalation/scalation_kernel/) on GitHub.
Installation requires a recent ScalaTion distribution (>= 1.3) from
[here](http://cobweb.cs.uga.edu/~jam/scalation.html). Make sure that
the `SCALATION_JARS` environment variable is set appropriately as
described in [General Instructions](#general-instructions) before
continuing. To install the development version of **Scalation Kernel**,
you can use the following commands:

```
$ git clone https://github.com/scalation/scalation_kernel.git
$ python3 -m pip install -U pip
$ python3 -m pip install -e scalation_kernel
$ python3 -m scalation_kernel.install
```

After installing ScalaTion Kernel, you may want to test it out
with Jupyter. To run Jupyter, you might use the following command:

```
$ python3 -m jupyter notebook
```

<hr>

Copyright (c) 2017 Michael E. Cotterell and the University of Georgia.
This software is free and open source under an
[MIT License](https://github.com/scalation/scalation_kernel/blob/master/LICENSE.md).
The content and opinions expressed on this Web page do not necessarily
reflect the views of nor are they endorsed by the University of Georgia or
the University System of Georgia.

