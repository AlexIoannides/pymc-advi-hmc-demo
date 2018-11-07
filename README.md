# MCMC & Variational Inference for Bayesian Data Analysis

Conducting a Bayesian data analysis - e.g. estimating a Bayesian linear regression model - will usually require some form of Probabilistic Programming Language (PPL). More often than not, PPLs implement Markov Chain Monte Carlo (MCMC) algorithms that allow one to draw samples and make inferences from the posterior distribution implied by the choice of model - the likelihood and prior distributions for its parameters - conditional on the observed data.

MCMC algorithms are, generally speaking, computationally expensive and do not scale very easily. Over the past few years, however, a new class of algorithms for inferring Bayesian models has been developed, that do not rely heavily on computationally expensive random sampling. These algorithms are referred to as Variational Inference (VI) algorithms and have been shown to be successful with the potential to scale to 'large' datasets.

My preferred PPL is PYMC3 and offers a choice of both MCMC and VI algorithms for inferring models in Bayesian data analysis. The purpose of this notebook is to demonstrate how they can both be used to perform a simple linear regression, and to then compare their results.

## Reproducing these Results - Managing Project Dependencies

We use [pipenv](https://docs.pipenv.org) for managing project dependencies and Python environments (i.e. virtual environments). All of the direct packages dependencies required to run the code (e.g. NumPy for arrays/tensors and Pandas for DataFrames), as well as all the packages used during development (e.g. Jupyter and IPython for interactive console and sessions and serving notebooks), are described in the `Pipfile`. Their **precise** downstream dependencies are described in `Pipfile.lock`.

### Installing Pipenv

To get started with Pipenv, first of all download it - assuming that there is a global version of Python available on your system and on the PATH, then this can be achieved by running the following command,

```bash
pip3 install pipenv
```

Pipenv is also available to install from many non-Python package managers. For example, on OS X it can be installed using the [Homebrew](https://brew.sh) package manager, with the following terminal command,

```bash
brew install pipenv
```

For more information, including advanced configuration options, see the [official pipenv documentation](https://docs.pipenv.org).

### Installing this Projects' Dependencies

Make sure that you're in the project's root directory (the same one in which the `Pipfile` resides), and then run,

```bash
pipenv install --dev
```

This will install all of the direct project dependencies as well as the development dependencies (the latter a consequence of the `--dev` flag).

### Running Python, IPython and JupyterLab from the Project's Virtual Environment

In order to continue development in a Python environment that precisely mimics the one the project was initially developed with, use Pipenv from the command line as follows,

```bash
pipenv run python3
```

The `python3` command could just as well be `ipython3` or the JupterLab, for example,

```bash
pipenv run jupyter lab
```

This will fire-up a JupyterLab *where the default Python 3 kernel includes all of the direct and development project dependencies*. This is how we advise that the notebooks within this project are used.

### Pipenv Shells

Prepending `pipenv` to every command you want to run within the context of your Pipenv-managed virtual environment, can get very tedious. This can be avoided by entering into a Pipenv-managed shell,

```bash
pipenv shell
```

which is equivalent to 'activating' the virtual environment. Any command will now be executed within the virtual environment. Use `exit` to leave the shell session.
