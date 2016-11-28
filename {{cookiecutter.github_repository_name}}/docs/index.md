#{{cookiecutter.github_repository_name}}


{{cookiecutter.description}}. Check out the project's [documentation](https://github.com/{{cookiecutter.github_username}}/{{cookiecutter.github_repository_name}}/).

# Prerequisites 
- [virtualenv](https://virtualenv.pypa.io/en/latest/)

# Initialize the project
Create and activate a virtualenv:

```bash
virtualenv env
source env/bin/activate
```
Install dependencies:

```bash
pip install -r requirements.txt
```
Initialize the git repository

```
git init
git remote add origin git@github.com:{{cookiecutter.github_username}}/{{cookiecutter.github_repository_name}}.git
```

Migrate, create a superuser, and run the server:
```bash
python {{cookiecutter.app_name}}/manage.py migrate
python {{cookiecutter.app_name}}/manage.py createsuperuser
python {{cookiecutter.app_name}}/manage.py runserver
```

# Create Servers
By default the included fabfile will setup three environments:

- dev -- The bleeding edge of development
- qa -- For quality assurance testing
- prod -- For the live application

Create these servers on Heroku with:

```bash
fab init
```

# Automated Deployment
Deployment is handled via Travis. When builds pass Travis will automatically deploy that branch to Heroku. Enable this with:
```bash
travis encrypt $(heroku auth:token) --add deploy.api_key
```
