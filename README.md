# This is a boilerplate app to get a django docker app up and running quickly.

## This bare bones app just has:
1. Django Web Server
2. Postgres DB

### Start the project by

```
python -m venv env
source env/bin/activate
pip install django==3.0.7
django-admin.py startproject {project_name} .
```

### Add this to the settings file
```
import os

DATABASES = {
    "default": {
        "ENGINE": os.environ.get("SQL_ENGINE"),
        "NAME": os.environ.get("SQL_DATABASE"),
        "USER": os.environ.get("SQL_USER"),
        "PASSWORD": os.environ.get("SQL_PASSWORD"),
        "HOST": os.environ.get("SQL_HOST"),
        "PORT": os.environ.get("SQL_PORT"),
    }
}
```

### create apps
```
docker-compose -f docker-compose.local.yml exec web python manage.py {app_name} app
```

### append to the settings file

```
STATIC_URL = "/staticfiles/"
STATIC_ROOT = os.path.join(BASE_DIR, "staticfiles")
```
