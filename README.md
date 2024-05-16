# python-project
Template for python projects

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
and the project may be re-installed via the [`Makefile`](./Makefile) per the [installation instruction](#Instruction).
