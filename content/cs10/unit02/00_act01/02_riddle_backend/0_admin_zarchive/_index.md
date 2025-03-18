---
Title: "[0. Model, DB & Admin]"
# draft: True

---

# Model, Databases, & Admin Portal

During the track lessons you will be creating a web app for the ISF Riddler. You should remember the Riddle database from the Networking Unit! 

---


## [0] Starter Code

{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd ~/desktop/making_with_code/cs10/unit_web_apps/
git clone https://github.com/the-isf-academy/lab_riddler_django_yourgithubusername
cd lab_riddler_django_yourgithubusername
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

---

## [1] The Model

{{< look-action >}}You can find the `Riddle` model in `riddle_app/models.py`.

{{< expand "riddle_app/models.py" >}}

```python
from django.db import models
from fuzzywuzzy import fuzz


class Riddle(models.Model):
    question = models.CharField(max_length=500)
    answer = models.CharField(max_length=500)
    likes = models.IntegerField(default=0)
    date_added = models.DateTimeField(auto_now_add = True)

    DIFFICULTY_CHOICES = [
        ('E', 'Easy'),
        ('M','Medium'),
        ('H', 'Hard'),
    ]

    difficulty = models.CharField(
        max_length=1,
        choices=DIFFICULTY_CHOICES,
        default=None,
    )

    def __str__(self):
        return f"{self.question}"
    
    def check_guess(self,guess):
        MIN_FUZZ_RATIO = 70
        similarity = fuzz.ratio(guess.lower(), self.answer.lower())
        
        if similarity >= MIN_FUZZ_RATIO:
            return True
        else:
            return False
        
    def increase_likes(self):
        self.likes += 1
        self.save()
```

{{< /expand >}}

{{< code-action >}} **Firstly, let's `migrate` our `Riddle` model into the database. Then, run the server.**
```shell
python manage.py migrate
python manage.py runserver   `
```

{{< code-action >}} **Visit [127.0.0.1:8000/](http://127.0.0.1:8000/) to view the app!** Since this lab focuses on the backend, you already have `html` and `css` files. 

---


## [2] Admin Portal

Just like other parts of our app, the Administration page is a route that is configured in Django. With Django's default project setup, the panel is automatically enabled.

As you can see in `riddle_app/admin.py` the `Riddle` model is registered. 

```python
from django.contrib import admin
from .models import Riddle

admin.site.register(Riddle)
```

{{< code-action >}} **We can now access the admin portal by going to: [`127.0.0.1:8000/admin/`](http://127.0.0.1:8000/admin/).**

If you go to this URL, there will be a webpage where we can log in to the admin site. **We need Superuser access to log in.**

---

### [Creating a Superuser Account]

We've successfully checked that the admin site is ready to go but we can't log in! We need to create a Superuser account to log into the admin site.


{{< code-action >}} **Create a SuperUser to access the admin portal.** You'll need to quit the server, then create the user.    
Remember, `control + C` quits the server.

```shell
python manage.py createsuperuser
```

Django will then prompt you to **enter a username and password and that user will have superuser access to the admin site**. For ease of use, keep your username and password short. You can also skip the email field with `return`. It will just ask you to type `y` to `Bypass password validation and create user`.
> It can be as simple as
> - username: `a`
> - password: `123`


{{< code-action >}} **Now, restart the server and login to the admin portal:** [`127.0.0.1:8000/admin/`](http://127.0.0.1:8000/admin/)


{{< code-action >}} **Explore the portal and add 3 riddles**


{{< aside "God View" >}}

As the owners and administrators of your website, you have access to your users' accounts and all of your users' data. We literally have a **god view of everything that is entered into our database**.

There are lots of ethical questions that need to be considered when building an app, and because of this, always remember the quote from Aunt May to Peter Parker...   

**With great power comes great responsibility!**

{{< /aside >}}

---

## [3] Riddle Model


{{< checkpoint >}}

✏️💻 **Follow along with the worksheet to understand writing and editing models in Django.** You will be working in:
- `models.py`
- `views.py`
- `riddle_app/riddle_detail.html`


{{</checkpoint>}}



{{< code-action >}}**When you change the model, you must update the database with `makemigrations`, apply the changes with `migrate`, and re-run the server.**

```shell
python manage.py makemigrations
python manage.py migrate
python manage.py runserver     
```

---

## [4] Deliverables 

{{< deliverables >}}
{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}

<!-- 
## [3] Django Shell

**Now that we have some data in our database, let's see what we can do with it!** We can try out different methods using the python shell. 


{{< code-action "Enter the shell." >}} You will need to quit the server to enter the shell.
```shell
python manage.py shell
```

{{< code-action " First, we can use the built-in capabilities of any Django model object." >}} You can read the official [Django Model Documentation](https://docs.djangoproject.com/en/4.1/topics/db/queries/) to learn more. 

> 💭 You should remember this from the Networking unit!


```python
>>> from riddle_app.models import Riddle
>>> Riddle.objects.all()
>>> Riddle.objects.count()
3
>>> Riddle.objects.first()
<Riddle: I’m the rare case when today comes before yesterday. What am I?>
>>> Riddle.objects.last()
<Riddle: I speak without a mouth and hear without ears. I have no body, but I come alive with wind. What am I?>
>>> Riddle.objects.get(id=1)
<Riddle: I’m the rare case when today comes before yesterday. What am I?>
```

{{< code-action " We can try printing out some of the `Riddle` properties" >}}

```python
>>> first_riddle = Riddle.objects.first()
>>> first_riddle.answer
'A question of time'
>>> first_riddle.question
'I’m the rare case when today comes before yesterday. What am I?'
>>> first_riddle.likes
47
```

---

### [Riddle Methods]

{{< look-action >}} **The `Riddle` model has 2 methods:** 
- `check_guess()`
- `increase_likes()`

{{< code-action >}} **Try and successfully use both methods in the shell.** One way to know if you were successful, is to check the admin portal and see if the `likes` property increases for a specific `Riddle`.

--- -->
<!-- 
## [4] Changing the Model

What if we decide we want to add more fields and methods to our `Riddle` model. It's possible with `makemigrations`. 

{{< code-action >}} **Make the following additions to the `Riddle` in `riddle_app/models.py`:**

**0. Add a field for number of guesses** 
    - which method should you incorporate this addition?

**1. Add a field for correct guesses**
    - which method should you incorporate this addition?

**2. Add a field for hints** 
    - in a future lab we will include this into your `NewRiddleForm`

---

{{< code-action >}}**Once you've changed the code, you will need to change the database with `makemigrations`.**
```shell
python manage.py makemigrations
python manage.py migrate
python manage.py runserver     
```



☑️ **Now, let's login to the admin portal to confirm your changes were made:** [`127.0.0.1:8000/admin/`](http://127.0.0.1:8000/admin/)

☑️ **Also, don't forget to use the `shell` to check if your changes to the `methods` were successful** -->


