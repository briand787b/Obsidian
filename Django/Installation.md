# Installation
## Project Initialization
1. Navigate to `~/django/` directory
2. Create project directory: `mkdir project_name`
3. Navigate to `~/django/project_name`
4. Create isolated environment: `python -m venv env` ('env' might depend on shell characteristics)
5. Activate the environment: `source env/bin/activate`
6. Install django in that venv: `pip install django`
7. Create the project: `django-admin startproject project_name`
8. Rename project to eliminate redundancy: `mv project_name src`
9. Create an app in the project: `python manage.py startapp app`

## Run the Server
1. Make migration(s): `python manage.py makemigrations`
2. Run migration(s): `python manage.py migrate`
3. Start server: `python manage.py runserver`

## Default Files
### Root
**manage.py** - This is a command-line utility used to interact with your project. It is a thin wrapper around the `django-admin.py` tool. You don't need to edit this file.
### Project
* ***__init__.py** - An empty file that tells Python to treat the `mysite` directory as a Python module.
* ***asgi.py** - This is the configuration to run your project as ASGI, the emerging Python standard for asynchronous web servers and applications.
* ***settings.py** - This indicates settings and configuration for your project and contains initial default settings.
* ***urls.py** - This is the place where your URL patterns live. Each URL defined here is mapped to a view.
* **wsgi.py** - This is the configuration to run your project as a Web Server Gateway Interface (**WSGI**) application.
### App
* **admin.py**: This is where you register models to include them in the Django administration site—using this site is optional.
- **apps.py**: This includes the main configuration of the `blog` application.
- **migrations**: This directory will contain database migrations of your application. Migrations allow Django to track your model changes and synchronize the database accordingly.
- **models.py**: This includes the data models of your application; all Django applications need to have a `models.py` file, but this file can be left empty.
- **tests.py**: This is where you can add tests for your application.
- **views.py**: The logic of your application goes here; each view receives an HTTP request, processes it, and returns a response.
