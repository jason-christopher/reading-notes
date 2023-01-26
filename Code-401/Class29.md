# Django Custom User

## Custom User Model

* The official Django documentation highly recommends using a custom user model instead. This provides far more flexibility down the line so, as a general rule, ***always use a custom user model for all new Django projects***.
* Creating our initial custom user model requires five steps:
  1. In `settings.py` we'll add the `accounts` app and use the `AUTH_USER_MODEL` config to tell Django to use our new custom user model in place of the built-in `User` model. We'll call our custom user model `CustomUser`. Within `INSTALLED_APPS` add `accounts` at the bottom. Then at the bottom of the entire file, add the `AUTH_USER_MODEL config`.

      ```python
      # django_project/settings.py
      INSTALLED_APPS = [
          "django.contrib.admin",
          "django.contrib.auth",
          "django.contrib.contenttypes",
          "django.contrib.sessions",
          "django.contrib.messages",
          "django.contrib.staticfiles",
          "accounts",  # new
      ]
      ...
      AUTH_USER_MODEL = "accounts.CustomUser"  # new
      ```

  2. Now update `accounts/models.py` with a new `User` model which we'll call `CustomUser`.

      ```python
      # accounts/models.py
      from django.contrib.auth.models import AbstractUser
      from django.db import models

      class CustomUser(AbstractUser):
          pass
          # add additional fields in here

          def __str__(self):
              return self.username
      ```

  3. We need new versions of two form methods that receive heavy use working with users. Stop the local server with `Control+c` and create a new file in the `accounts` app called `forms.py` with `(accounts) $ touch accounts/forms.py`. We'll update it with the following code to largely subclass the existing forms.

      ```python
      # accounts/forms.py
      from django import forms
      from django.contrib.auth.forms import UserCreationForm, UserChangeForm

      from .models import CustomUser

      class CustomUserCreationForm(UserCreationForm):

          class Meta:
              model = CustomUser
              fields = ("username", "email")

      class CustomUserChangeForm(UserChangeForm):

          class Meta:
              model = CustomUser
              fields = ("username", "email")
      ```

  4. Finally we update `admin.py` since the Admin is highly coupled to the default User model.

      ```python
      # accounts/admin.py
      from django.contrib import admin
      from django.contrib.auth.admin import UserAdmin

      from .forms import CustomUserCreationForm, CustomUserChangeForm
      from .models import CustomUser

      class CustomUserAdmin(UserAdmin):
          add_form = CustomUserCreationForm
          form = CustomUserChangeForm
          model = CustomUser
          list_display = ["email", "username",]

      admin.site.register(CustomUser, CustomUserAdmin)
      ```
  
  5. We can now run `makemigrations` and `migrate` for the first time to create a new database that uses the custom user model.

      ```python
      (.venv) > python manage.py makemigrations accounts
      (.venv) > python manage.py migrate
      ```

Source: <https://learndjango.com/tutorials/django-custom-user-model>

## DjangoX

### Installation

* DjangoX can be installed via Pip, Pipenv, or Docker. To start, clone the repo to your local computer and change into the proper directory.

  ```
  $ git clone https://github.com/wsvincent/djangox.git
  $ cd djangox

  $ source .venv/bin/activate

  (.venv) $ pip install -r requirements.txt
  (.venv) $ python manage.py migrate
  (.venv) $ python manage.py createsuperuser
  (.venv) $ python manage.py runserver
  # Load the site at http://127.0.0.1:8000
  ```

* The `INTERNAL_IPS` configuration in `django_project/settings.py` must be also be updated:

  ```python
  # config/settings.py
  # django-debug-toolbar
  import socket
  hostname, _, ips = socket.gethostbyname_ex(socket.gethostname())
  INTERNAL_IPS = [ip[:-1] + "1" for ip in ips]
  ```

* Add environment variables. There are multiple packages but I personally prefer `environs`.
* Add `gunicorn` as the production web server.
* Update the `EMAIL_BACKEND` and connect with a mail provider.
* Make the `admin` more secure.
* `django-allauth` supports social authentication if you need that.

Source:<https://github.com/wsvincent/djangox>

## Things I Want To Know More About

* Pros/cons of using DjangoX.
