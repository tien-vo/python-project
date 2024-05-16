# python-project
Template for python projects. To use this template, create a repository with
this template, change relevant names for the project and development package,
and follow installation instructions.

## Installation

### Overview

External libraries and `python-poetry` are managed by `micromamba` via [`conda-lock.yml`](./conda-lock.yml). Python packages are managed by `python-poetry` via [`poetry.lock`](./poetry.lock).

### Build dependencies

- micromamba
- cmake

To get started, first install `micromamba` with
```
$ "${SHELL}" <(curl -L micro.mamba.pm/install.sh)
```
or through any other method listed in the [installation guide](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html).

Make sure `cmake` and `micromamba` can be found in the system path and the latter configured in the shell.

### Instruction

Install the project with
```
$ make install
```

## Development post-installation

### Package development

Take some time to familiarize with the [`pyproject.toml`](./pyproject.toml),
which is where most of your Python dependencies are specified. The
[src/pyproject](./src/pyproject/) directory is where your development package is
located. If everything installs correctly, 
```
$ micromamba run -n python-project python -m pyproject
```
should return
```
Hello world!
```
The default project name "python-project" may be changed in the
[`Makefile`](./Makefile) and [`pyproject.toml`](./pyproject.toml). The default
package name "pyproject" may be changed in [`pyproject.toml`](./pyproject.toml).

### Dependency specification

Library dependencies may be specified in [`environment.yml`](./environment.yml). For example, to install `openmpi`, specify
```
# environment.yml
dependencies:
  - ...
  - openmpi
```
For available libaries, use the `micromamba search` command or search the [website](https://conda-forge.org/packages/).

The [`conda-lock.yml`](./conda-lock.yml) file can then be generated with `conda-lock` by the following command
```
$ conda-lock -f environment.yml
```
Then, the project may be re-installed via the [`Makefile`](./Makefile) per the [installation instruction](#Instruction).

Python dependencies may be specified interactively with `poetry`. For example,
to use `numpy`, do
```
$ poetry add numpy
```
The lock file will be updated automatically by `poetry`.
