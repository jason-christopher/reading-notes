# Django REST Framework & Docker

## Docker Introduction

* With Docker, the entire development environment is isolated: programming language, software packages, databases, and more. We no longer have to mess around with virtual environments. We can faithfully reproduce a production environment locally and Docker can be shared among team members so everyone is working on the same setup. The downside is complexity.

### Linux Containers

* Docker is really just ***Linux containers*** which are a type of virtualization.
* Virtualization and specifically virtual machines are complete copies of a computer system from the operating system on up.
* The downside to a virtual machine is size and speed. A typical guest operating system can easily take up 700MB of size. So if one physical server supports three virtual machines, that’s at least 2.1GB of disk space taken up along with separate needs for CPU and memory resources.
* Most computers rely on the same Linux operating system. Virtualizing from the operating system level up would provide a lightweight, faster way to duplicate much of the same functionality.
* In recent years ***Linux containers***, also known as “*containerization*,” has become increasingly popular. For most applications, a virtual machine provides far more resources than are needed and a container is more than sufficient.
* Docker is a way to implement Linux containers. An analogy we can use here is that of homes and apartments. Virtual Machines are like homes: stand-alone buildings with their own infrastructure including plumbing and heating, as well as a kitchen, bathrooms, bedrooms, and so on. Docker containers are like apartments: they share common infrastructure like plumbing and heating, but come in various sizes that match the exact needs of an owner.

### Containers vs Virtual Environments

* Virtual environments are used to isolate Python software packages locally. We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer.
* But virtual environments can only isolate Python packages. They still rely on a global, system-level installation of Python albeit they can refer to the proper version. So when we use Python 2.7 in a project, we’re pointing to an installation of Python 2.7 on the computer itself, not actually within the virtual environment.
* We can’t run a production database or other services within virtual environments so compared to Docker containers they are far more limited.

### Images and Containers

* ***Images*** and ***containers*** are the two fundamental concepts to grasp when you start with Docker.
  * An image is a snapshot in time of what a project contains.
  * A container is a running instance of the image.
* A baking analogy we can use here is as follows:
  * A `Dockerfile` is the recipe for a cake
  * An image is a snapshot of the recipe at a given time
  * A `docker-compose.yml` says how to make the cake
  * And the container is the actual, baked cake

### Takeaways

The important takeaways are:

* Docker is a way to run Linux containers
* Containers are a lightweight alternative to Virtual Machines
* `Dockerfile` is a list of instructions for creating an image
* Images are made up of one or more layers
* Containers are a running instance of an image
* `docker-compose.yml` controls how to run the container
* Containers are stateless and ephemeral in nature. We can link the local filesystem via `volumes` but things become more complex with databases.

Source: <https://wsvincent.com/beginners-guide-to-docker/>

## Django for APIs - Library Website

* Django REST Framework works alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.
* The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

### Traditional Django

* A traditional Django website consists of a single project with multiple apps representing discrete functionality.

### First App

* Run the `startapp` command `python manage.py startapp books` to create the app.
* Each app has a `__init__.py` file identifying it as a Python package and there are 6 new files created:
  * `admin.py` is a configuration file for the built-in Django Admin app
  * `apps.py` is a configuration file for the app itself
  * `migrations/` is a directory that stores migrations files for database changes
  * `models.py` is where we define our database models
  * `tests.py` is for our app-specific tests
  * `views.py` is where we handle the request/response logic for our web app
* Typically, developers will also create a `urls.py` file within each app for routing.
* Before moving on we must add our new app to the `INSTALLED_APPS` configuration in the `django_project/settings.py` file.

### Models

* In the `books/models.py` file, `models` is imported from Django on the top line and a new class, called `Book`, extends it. There are four fields: `title`, `subtitle`, `author`, and `isbn`. We also include a `__str__` method so that the title of a book will display in readable format in the admin later on.
* Run the following commands: `python manage.py makemigrations books` and `python manage.py migrate`.

### Admin

* On the command line run `python manage.py createsuperuser` and follow the prompts to enter a username, email, and password. Note that for security reasons, text will not appear on the screen while entering your password.
* Update our books app’s `admin.py file`:

    ```python
    # books/admin.py
    from django.contrib import admin

    from .models import Book

    admin.site.register(Book)
    ```

### Views

* The `views.py` file controls how the database model content is displayed. Since we want to list all books we can use the built-in generic class ***ListView***. Update the `books/views.py` file:

    ```python
    # books/views.py
    from django.views.generic import ListView

    from .models import Book


    class BookListView(ListView):
        model = Book
        template_name = "book_list.html"
    ```

### URLs

* We need to set up both the project-level `urls.py` file and then one within the `books` app. When a user visits our site they will initially interact with the `django_project/urls.py` file so let’s configure that one first. Add the `include` import on the second line and then a new path for the `books` app.

    ```python
    # django_project/urls.py
    from django.contrib import admin
    from django.urls import path, include  # new

    urlpatterns = [
        path("admin/", admin.site.urls),
        path("", include("books.urls")),  # new
    ]
    ```

### Templates

* The final step is to create our template file that controls the layout on the actual web page. We have already specified its name as `book_list.html` in our view. There are two options for its location: by default the Django template loader will look for templates within our `books` app in the following location: `books/templates/books/book_list.html`. We could also create a separate, project-level templates directory instead and update our `django_project/settings.py` file to point there.

Source: <https://djangoforapis.com/library-website-and-api/>

## REST, Hypermedia & HATEOAS

### Building Hypermedia APIs with REST framework

* REST framework is an agnostic Web API toolkit. It does help guide you towards building well-connected APIs, and makes it easy to design appropriate media types, but it does not strictly enforce any particular design style.

### What REST framework provides

* It is self evident that REST framework makes it possible to build Hypermedia APIs. The browsable API that it offers is built on HTML - the hypermedia language of the web.
* REST framework also includes serialization and parser/renderer components that make it easy to build appropriate media types, hyperlinked relations for building well-connected systems, and great support for content negotiation.

### What REST framework doesn't provide

* What REST framework doesn't do is give you machine readable hypermedia formats such as HAL, Collection+JSON, JSON API or HTML microformats by default, or the ability to auto-magically create fully HATEOAS style APIs that include hypermedia-based form descriptions and semantically labelled hyperlinks. Doing so would involve making opinionated choices about API design that should really remain outside of the framework's scope.

Source: <https://www.django-rest-framework.org/topics/rest-hypermedia-hateoas/>

## What I Want To Learn More About

* Use of Docker in an actual project. The Django reading was stuff we covered last week.
