---
Title: 3.B.2 Using the Admin Page
draft: True

---

# Using the Admin Page

Now that we have successfully added data into our app, it would be great if we had some way to access it.

Well, Django has a build-in administration page that allows us to look at the data in our database!

## [A] Admin Page on Django

Just like other parts of our app, the Administration page is a route that is configured in Django. With Django's default project setup, the panel is automatically enabled.


{{< code-action >}} To confirm the admin panel is ready to go, first check the `base.py` file under the `cs10_webapp_base/settings` directory. We need to make sure there the admin interface is installed. If this code isn't in `base.py`, you will need to copy and paste this code in. Django should have already added this for us by default.

```python {hl_lines=["2"]}
INSTALLED_APPS = [
    'django.contrib.admin',
    # other installed apps go here...
]
```

{{< code-action >}} Next, we need to confirm the following import statement is in the `admin.py` file. If not, add it in.

```shell
from django.contrib import admin
```


{{< code-action >}} **We can now access the admin portal by going to: `http://127.0.0.1:8000/admin/`.**

If you go to this URL, there will be a webpage where we can log in to the admin site. We will need Superuser access for this.

## [B] Creating a Superuser Account

We've successfully checked that the admin site is ready to go but we can't log in! We need to create a Superuser account to log into the admin site.


{{< code-action >}} To create a Superuser for our website, quit the Django server and in the same path, type in Terminal:

```shell
python3 manage.py createsuperuser
```

Django will then prompt you to enter a username and password and that user will have superuser access to the admin site. We can then restart the server and access the admin site using the superuser account.

## [C] Using the Admin Site to Access Data in the Database

By default, the Django admin site doesn't allow us to do much. We can play around with user groups and user accounts.

### [Registering our Models]

If we want to look at our Task data, we can register our models in `admin.py` and Django will give access to our data through the admin page. The `admin.py` file can be found in the `starter_app` directory.


{{< code-action >}} Let's register the Task model so we can see our Task data from within the admin page.

```python {hl_lines=["2-4"]}
from django.contrib import admin
from .models import Task

admin.site.register(Task)
```
These lines of code will enable us to access the data in the Task database. We can create/update/delete tasks here as well.

Just make sure to refresh the admin page to see the changes.

### [Remember Aunt May...]

As the owners and administrators of your website, you have access to your users' accounts and all of your users' data. We literally have a "God" view of everything that is entered into our database.

There are lots of ethical questions that need to be considered when building an app, and because of this, always remember the quote from Aunt May to Peter Parker...   

**With great power comes great responsibility!**

<br>

<!-- {{< checkpoint >}}

Answer the section 'C' questions in your `Django Backend Worksheet` Google Doc.

{{</checkpoint >}} -->
