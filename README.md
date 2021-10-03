[![PyPI status](https://img.shields.io/pypi/status/kiara_modules.language_processing.svg)](https://pypi.python.org/pypi/kiara_modules.language_processing/)
[![PyPI version](https://img.shields.io/pypi/v/kiara_modules.language_processing.svg)](https://pypi.python.org/pypi/kiara_modules.language_processing/)
[![PyPI pyversions](https://img.shields.io/pypi/pyversions/kiara_modules.language_processing.svg)](https://pypi.python.org/pypi/kiara_modules.language_processing/)
[![Build Status](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2FDHARPA-Project%2Fkiara%2Fbadge%3Fref%3Ddevelop&style=flat)](https://actions-badge.atrox.dev/DHARPA-Project/kiara_modules.language_processing/goto?ref=develop)
[![Coverage Status](https://coveralls.io/repos/github/DHARPA-Project/kiara_modules.language_processing/badge.svg?branch=develop)](https://coveralls.io/github/DHARPA-Project/kiara_modules.language_processing?branch=develop)
[![Code style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

# *kiara* modules (language_processing)

A set of modules (and pipelines) for [*Kiara*](https://github.com/DHARPA-project/kiara).

 - Documentation: [https://dharpa.org/kiara_modules.language_processing](https://dharpa.org/kiara_modules.language_processing)
 - Code: [https://github.com/DHARPA-Project/kiara_modules.language_processing](https://github.com/DHARPA-Project/kiara_modules.language_processing)

## Description

TODO

## Development

### Requirements

- Python (version >=3.6 -- some make targets only work for Python >=3.7 though)
- pip, virtualenv
- git
- make (on Linux / Mac OS X -- optional)


### Prepare development environment

If you only want to work on the modules, and not the core *Kiara* codebase, follow the instructions below. Otherwise, please
check the notes on how to setup a *Kiara* development environment under (TODO).

#### Linux & Mac OS X (using make)

For *NIX-like operating system, setting up a development environment is relatively easy:

```console
git clone https://github.com/DHARPA-Project/kiara_modules.language_processing.git
cd kiara_modules.language_processing
python3 -m venv .venv
source .venv/bin/activate
make init
```

#### Windows (or manual pip install)

It's impossible to lay out all the ways Python can be installed on a machine, and virtual- (or conda-)envs can be created, so I'll assume you know how to do this.
One simple way is to install the [Anaconda (individual edition)](https://docs.anaconda.com/anaconda/install/index.html), then use the Anaconda navigator to create a new environment, install the 'git' package in it (if your system does not already have it), and use the 'Open Terminal' option of that environment to start up a terminal that has that virtual-/conda-environment activated.

Once that is done, `cd` into a directory where you want this project folder to live, and do:

```console
# make sure your virtual env is activated!!!
git clone https://github.com/DHARPA-Project/kiara_modules.language_processing.git
cd kiara_modules.language_processing
pip install --extra-index-url https://pypi.fury.io/dharpa/ -U -e .[all_dev]
```

#### Try it out

After this is done, you should be able to run the included example module via:

```console
# for now we need to install required spacy modules manually:
python -m spacy download it_core_news_sm
# then, using the data from the TopicModeling repository:
kiara run -e topic_modelling_end_to_end path=path/to/data_tm_workflow earliest="1919-01-01" latest="2000-01-01" languages=italian languages=german compute_coherence=true
...
...
```

### Re-activate the development environment

The 'prepare' step from above only has to be done once. After that, to re-enable your virtual environment,
you'll need to navigate to the directory again (wherever that is, in your case), and run the ``source`` command from before again:

```console
cd path/to/kiara_modules.language_processing
source .venv/bin/activate  # if it isn't activated already, for example by the Anaconda navigator
kiara --help  # or whatever, point is, kiara should be available for you now,
```

### ``make`` targets (Linux & Mac OS X)

- ``init``: init development project (install project & dev dependencies into virtualenv, as well as pre-commit git hook)
- ``update-dependencies``: update development dependencies (mainly the core ``kiara`` package from git)
- ``flake``: run *flake8* tests
- ``mypy``: run mypy tests
- ``test``: run unit tests
- ``docs``: create static documentation pages (under ``build/site``)
- ``serve-docs``: serve documentation pages (incl. auto-reload) for getting direct feedback when working on documentation
- ``clean``: clean build directories

For details (and other, minor targets), check the ``Makefile``.


### Running tests

``` console
> make test
# or
> make coverage
```


## Copyright & license

This project is MPL v2.0 licensed, for the license text please check the [LICENSE](/LICENSE) file in this repository.

[Copyright (c) 2021 DHARPA project](https://dharpa.org)
