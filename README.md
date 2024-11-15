# NB-N-gram
This is the official repository of [NB N-Gram](http://www.nb.no/sp_tjenester/beta/ngram_1/), created by [Språkbanken](http://www.nb.no/Tilbud/Forske/Spraakbanken) at the [National Library of Norway](http://www.nb.no/). In its current form NB N-gram is a trend viewer, similar to [Google Ngram Viewer](https://books.google.com/ngrams). It shows you the development of words or sequences of words in the vast material digitized at the National Library of Norway, but it is also perfectly adoptable to other corpora. This repository contains both the backend, written in Python/Flask, and the frontend, written in HTML/JavaScript.

## Install

To install necessary python dependencies in a virtual environment, we recommend using a project manager like [uv](https://docs.astral.sh/uv/) or [pdm](https://pdm-project.org/en/latest/), which must be installed separately. From your local clone of this repo, just run ```uv sync``` or ```pdm install```. 

If you prefer installing dependencies with [pip](https://pip.pypa.io/en/stable/), create a virtual environment, activate it and install the dependencies in `requirements.txt`:

```shell 
source .venv/bin/activate
pip install -r requirements.txt
```

## Run N-gram app

The app can be run with remote or local data sources.

### Local data source

1. Download the SQLite databases from [Språkbanken's repository](https://www.nb.no/sprakbanken/ressurskatalog/oai-nb-no-sbr-76/) or provide your own data
2. Configure the paths to the databases and the database schema in `backend.py`
3. Set the environment variable `FLASK_NGRAM_SETTINGS` to point to your Flask configuration file (eg. different settings for production and development machines): an example development configuration file is found in `flask-example-devsettings.cfg`
4. Start the session with `python backend.py`, listens at 127.0.0.1:5000 per default (for development only!) or run it behind a WSGI server like UWSGI or Gunicorn (production use)

### Remote data source
> **Note!** This version of the app is a work in progress. 

<!-- TODO
    - Add command to run with uv or pdm or poetry 
    - Add python script that fetches data with the API. 
--> 

This command will expose the app to port 5000 per default, and is for **development only**:

```shell 
[uv|pdm] run flask --app nb_n_gram.app run 
```

You can also run the app with a WSGI server like UWSGI or Gunicorn for  production deployment: 

```shell 
uv run gunicorn nb_n_gram.app:app run
```

## License
NB N-gram is released under the Apache 2.0 license.
