# cookiecutter-mlpoc
Cookiecutter template for Machine Learning Proof of Concept


## Features
* ✅ Development enviroment management with Docker
  * You can easily reproduce your environment even on AWS EC2, GCP, ...
* ✅ Dependency tracking using poetry
* ✅ Online demo template provided by GoogleColab and Streamlit
* ✅ Linting provided by flake8
* ✅ Formatting provided by black and isort
* ✅ CI with Github Actions

## Quick Start
1. Install the latest Cookiecutter if you haven't installed it yet (this requires Cookiecutter 1.4.0 or higher):

```shell
pip install -U cookiecutter
```

2. Generate a Python package project:

```shell
cookiecutter https://github.com/tyo-yo/cookiecutter-mlpoc
```

3. Create a repo and put it there

4. Setup your developemntal environment
  * Using Docker (Recommended):
```
docker build . -t {{ cookiecutter.project_slug }}
```
  * Using poetry:
    * First, you should install dependencies other than python dependencies like MeCab
    * Install python packages:
```
poetry install
```

5. Get your code on!
   * Your main component like model should be under ``project_slug/``
   * Visualization like data analysis can be made by jupyter notebook: ``notebooks/``
   * Dataset should be on cloud like AWS S3 or Google Storage for reproducibility
     * When dataset is too large, consider caching or saving it under ``data/``
   * When writing training code, you should use Comet.ml for managing experiments
     * experimental result like saved model should be under ``experiments/``
   * Some command-line utility like profile your code should be under ``scripts/``
     * [Typer](https://typer.tiangolo.com) would supports building CLI
   * You should write test to make sure there are no bugs: ``tests/``
