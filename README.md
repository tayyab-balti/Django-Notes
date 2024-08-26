# Django Project Setup Guide

This guide provides a step-by-step process for setting up a Django project, including project creation, app configuration, and key concepts.

## Table of Contents
1. [Setup and Installation](#setup-and-installation)
2. [Project Structure](#project-structure)
3. [Migrations](#migrations)
4. [Running the Server](#running-the-server)
5. [MVT Architecture](#mvt-architecture)
6. [Geeky Steps](#geeky-steps)
7. [Quick Summary](#quick-summary)
8. [Step by Step Guide](#step-by-step-guide)

   
## Setup and Installation

```bash
# Install Django
pip install django

# Create Django project
django-admin startproject myproject

# Navigate to the project directory
cd myproject

# Start a new app in the project
python manage.py startapp course
```


## Project Structure

- `myproject/`: Root directory
  - `manage.py`: Command-line utility
  - `myproject/`: Project Configuration
    - `__init__.py`: Python package indicator
    - `settings.py`: Project settings
    - `urls.py`: URL declarations
    - `wsgi.py`: WSGI entry-point (web servers gateway interface)
      
  - `course/`: Application directory
  - `migrations/`: Database migrations
  - `models.py`: Database models (classes in OOP)
  - `views.py`: Request/response logic (functions)
  - `admin.py`: Admin interface config
  - `apps.py`: App configuration
  - `tests.py`: Test definitions


## Migrations

```bash
# Make migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate
```


## Running the Server

```bash
# Run the development server
python manage.py runserver
```


## MVT Architecture

```bash
1. User sends a request to a URL
2. Django's URL dispatcher maps the URL to a specific View
3. View interacts with Models to fetch/manipulate data
4. View then renders a Template, passing it any required data
5. Rendered Template is sent back to the user as an HTTP response
```


## Geeky Steps

### 1) Create Django Project
    
        django-admin startproject myproject
        cd myproject

### 2) Start a New App
    
        python manage.py startapp course

### 3) Configure App in Project Settings
- Edit settings.py:
    ```python
    INSTALLED_APPS = [
        # ...
        'course',
    ]
    ```


### 4) Create Views 
- In views.py:
    
    ```python
    from django.http import HttpResponse

    def learn_django(request):
        return HttpResponse("Hello Django")

    def learn_python(request):
      return HttpResponse('<h2>Hello Python</h2>')
    ```


### 5) Configure URLs
- Create urls.py file in app folder
- In app's urls.py:

    ```python
    from django.urls import path
    from . import views

    urlpatterns = [
        path('learndj/', views.learn_django),
        path('learnpy/', views.learn_python),
    ]
    ```
- In project's urls.py: 

    ```python 
    from django.urls import path, include

    urlpatterns = [
        path('cor/', include('course.urls')),
    ]
    ```


### 6) Set Up Templates 
- Create templates folders in app and project root
- Configure settings.py: 

    ```python
    TEMPLATE_DIR = BASE_DIR / 'templates'
    TEMPLATES = [{
        'DIRS': [TEMPLATE_DIR],
        'APP_DIRS': True,
        # ...
        }]
    ```


### 7) Static Files
- Create static folder in project root
- Configure settings.py:

    ```python
    # STATIC_URL is the base URL location for serving static files
    STATIC_URL = 'static/'
    
    # STATICFILES_DIRS is a list of folders where Django will also look for static files
    STATIC_DIR = BASE_DIR / 'static'
    STATICFILES_DIRS = [STATIC_DIR]
    
    # STATIC_ROOT is the directory where static files will be collected when you run `collectstatic`
    STATIC_ROOT = BASE_DIR / "staticfiles"
    ```
- Use in Template files:
    ```python
    - First Load Static Files
    - Reference Static Files
    
    {% load static %}

    <link href="{% static 'myapp/css/styles.css' %}">
    <img src="{% static 'myapp/images/logo.png' %}" alt="Site Logo">
    <script src="{% static 'myapp/js/scripts.js' %}"></script>
    ```

        
## Quick Summary
- Create project: django-admin startproject myproject
- Create app: python manage.py startapp course | django-admin startapp course
- Configure app in settings.py
- Set up templates and static files
- Create views in views.py
- Configure URLs in urls.py
- Create templates and static files
- Run migrations and start serve


## Step by Step Guide
- Create a Virtual-Environment: python -m venv env_name
- Activate Virtual-Environment: env_name\Scripts\activate
- Create project: django-admin startproject myproject
- Navigate to the project directory: cd myproject
- Start a new app in the project: python manage.py startapp course
- Add/Install Applications to Django Project (course and fees to myproject) using settings.py INSTALLED_APPS
- Create templates folder inside each application and inside Root Project Folder
- Check 'APP_DIRS' : True in settings.py
- Add templates directory which is inside Root Project Folder, in settings.py
- Create folder inside app/templates directory for template files
- Create template files inside app/templates/folder
- Create template files inside templates folder which is inside Root Project Folder
- Add templates in settings.py. 
- Create static folder inside Root Project Folder
- Create css, js, images, videos, etc inside static folder
- Create static files inside css, js, images, videos, etc folder
- Add static in settings.py. 
- Write View Function inside views.py file
- Define url for view function of application using urls.py file
- Write Template file code
- Write Static file code
