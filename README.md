Welcome to the Content Suggestion Project! This web app will allow you to find inspiration for Instagram posts, popular hashtags and give you an analysis of your audience behavior. Note: You need to use your login credentials to Instagram, since the data is fetched using Instagram API.

You have two options to access this project: through Heroku and by manually downloading and running locally.

## Heroku Deployment

The link to the Heroku website: https://content-suggestion.herokuapp.com/ (deprecated)

## Run Virtual Environment

Virtual environment is a key component in ensuring that the application is configured in the right environment

##### Requirements
* Python 3
* Pip 3

```bash
$ brew install python3
```

Pip3 is installed with Python3

##### Installation
To install virtualenv via pip run:
```bash
$ pip3 install virtualenv
```

##### Usage
Creation of virtualenv:

    $ virtualenv -p python3 venv

If the above code does not work, you could also do

    $ python3 -m venv venv

To activate the virtualenv:

    $ source venv/bin/activate

Or, if you are **using Windows** - [reference source:](https://stackoverflow.com/questions/8921188/issue-with-virtualenv-cannot-activate)

    $ venv\Scripts\activate

To deactivate the virtualenv (after you finished working):

    $ deactivate

Install dependencies in virtual environment:

    $ pip3 install -r requirements.txt

## Environment Variables

All environment variables are stored within the `.env` file and loaded with dotenv package.

**Never** commit your local settings to the Github repository!

## Run Application

Start the server by running:

    $ export FLASK_ENV=dev
    $ export FLASK_APP=web
    $ python3 -m flask run
    
If **using Windows**, use 'set' instead of 'export'

## Unit Tests
To run the unit tests use the following commands:

    $ python3 -m venv venv_unit
    $ source venv_unit/bin/activate
    $ pip install -r requirements-unit.txt
    $ export FLASK_ENV=test
    $ export DATABASE_URL='sqlite:///web.db'
    $ export SECRET_KEY='testing_key'
    $ pytest unit_test

## Integration Tests

To run integration tests you need to start your containers and then run tests:

    $ python3 -m venv venv_integration
    $ source venv_integration/bin/activate
    $ pip3 install -r requirements-integration.txt
    $ export FLASK_ENV=test
    $ export DATABASE_URL="mysql+pymysql://root:test_password@127.0.0.1:3306/main"
    $ docker-compose build --no-cache
    $ docker-compose up -d --force-recreate
    $ pytest integration_test
    $ docker-compose down

## Flask-Migrate

Flask-Migrations is an extensions that manages DB migrations, common commands:

flask db migrate (create migration)
flask db upgrade (implement migration in the DB)
