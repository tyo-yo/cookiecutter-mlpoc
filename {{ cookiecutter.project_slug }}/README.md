# {{ cookiecutter.project_name}}
![Tests](https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/workflows/Tests/badge.svg)  [![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


{{ cookiecutter.project_short_description }}

## Usage
```shell
git clone https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}.git
cd {{ cookiecutter.project_slug }}

docker run --rm -it -v $PWD:/{{ cookiecutter.project_slug }} --env-file .env --gpus all docker.pkg.github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/{{ cookiecutter.project_slug }}:latest bash
docker run --rm -it -v $PWD:/{{ cookiecutter.project_slug }} -p 11111:11111 --env-file .env --gpus all docker.pkg.github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/{{ cookiecutter.project_slug }}:latest streamlit run --server.port 11111 app.py
docker run --rm -it -v $PWD:/{{ cookiecutter.project_slug }} -p 11111:11111 --env-file .env --gpus all docker.pkg.github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/{{ cookiecutter.project_slug }}:latest jupyter lab --port=11111 --ip=0.0.0.0 --no-browser --allow-root
```


## Quick Start (for owner)
1. Setup your developemntal environment
  * Using Docker (Recommended):
```
# If you update python dependencies, you should re-build docker image
docker build . -t  {{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/{{ cookiecutter.project_slug }}
```
  * Using poetry:
    * First, you should install dependencies other than python dependencies like MeCab
    * Install python packages:
```
poetry install
```

2. Create your own .env file and put your secret information like API key

3. Get your code on!
   * Your main component like model should be under ``{{ cookiecutter.project_slug }}/``
   * Visualization like data analysis can be made by jupyter notebook: ``notebooks/``
   * Dataset should be on cloud like AWS S3 or Google Storage for reproducibility
     * When dataset is too large, consider caching or saving it under ``data/``
   * When writing training code, you should use Comet.ml for managing experiments
     * experimental result like saved model should be under ``experiments/``
   * Some command-line utility like profile your code should be under ``scripts/``
     * [Typer](https://typer.tiangolo.com) would supports building CLI
   * You should write test to make sure there are no bugs: ``tests/``

http://colab.research.google.com/github/{{ cookiecutter.github_username }}/{{ cookiecutter.project_slug }}/blob/main/notebooks/demo-colab-streamlit.ipynb
