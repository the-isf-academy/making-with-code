---
Title: 3.B.4 Relational Databases
draft: True

---

# Relational Databases

So far, we have a To-Do app that allows us to keep track of tasks and users. People log in, post a new task on the system and everyone can see all the tasks. In essence, we have successfully built a "Job Post" website where everyone can see all the "Jobs".

But that's not the vision of the To-Do app.

## [A] Our Simple Database

We want a To-Do app where the tasks are private to the user. To do that, we need to take care of the following issues:
1. We can only create "tasks" publicly.
2. We don't want users to see the Tasks assigned to other users.

So, how do we make sure tasks are private to the user?

Currently, our User and Task models looks like this.
![Users and Tasks Table](/images/courses/cs10/unit02/users_tasks.png)

{{<checkpoint>}}
What changes can we make to "link" the two tables together?
{{</checkpoint>}}


If you answered, "Why don't we make a big table with all the data in it", this solution can potentially work. Your table could look like this.

{{< figure src="/images/courses/cs10/unit02/users_tasks_combined.png" width="220px" >}}

Technically speaking, we *can* make this table and use to to solve our Task-to-User problem. But there are problems here.

{{<checkpoint>}}
What is wrong with using this "new" User_Task table?
{{</checkpoint>}}

Here are a couple of expensive 'wrongs' about this table:
- We are duplicating the User table and its data in another table. This is very wasteful in terms of space.
- Because we duplicated the User table into the Task table, the table is needlessly big and searching through a big database table is slow, performance-wise.

Just these two issues should raise some alarm bells for us as programmers. In other words, we can do better. But how?


## [B] What is a Relational Database

Right now, our system has two tables that have no data connections with each other. This is what is called a ***simple database***.

{{<hint>}}
A ***simple database*** is a database where tables are distinct data collections with no data connections between the tables.
{{</hint>}}

For us to solve our initial problem, we need to connect the User and Task tables together. We need a ***relational database***.

{{<hint>}}
A ***relational database*** is a database where there are tables that can be linked together with common data.
{{</hint>}}


(Note: the ID field in the Users table and the ID field in the Task table are different IDs)

We want to somehow connect User and Task tables together to convert our simple database to a relational base. We can modify our current database to accommodate this "link". It's quite easy to do.

{{<checkpoint>}}
What would be the best data to use to accommodate this link?
{{</checkpoint>}}

We have a few choices here. We can use whatever is unique to the user account. Depending on our business logic, we can use either id, username or email. For the next steps, we will use id and username.

### [Adding User ID in the Task Table]

Adding id and username to the Task table is actually quite easy. All we need to do is to add a few lines of code in our Task model and then do a migration. Easy peasy!

{{< code-action >}} **Let's go into our `models.py` file and add the following lines.**

```python {hl_lines=["6","18"]}
import datetime
from django.db import models
from django.utils import timezone
from django.utils.timezone import now
from .validators import validate_caps
from django.contrib.auth.models import User


class Task(models.Model):
    title = models.CharField(max_length=30, validators=[validate_caps])
    label = models.CharField(max_length=8)
    notes = models.TextField(editable=True, max_length=200)

    due_date = models.DateField('Date Due', editable=True)
    pub_date = models.DateTimeField('Date Created',default=now, editable=False)
    archive = models.BooleanField(default=False)

    task_user = models.ForeignKey(User, on_delete=models.CASCADE, default=1)

    def __str__(self):
        return self.title

    def date_created(self):
        return self.pub_date >= timezone.now() - datetime.timedelta(days=1)
```

Let's go over these lines of code in detail.

- *task_user* will set a *ForeignKey* in our Task table which will be the field that "links" the Task and User tables together. We are using the default User model from Django. There more detailed explanation of what *ForeignKey* does in the Django documentation. *ForeignKey* sets up many-to-one relationships between (many) Tasks and (one) User.
- The parameters for *ForeignKey* can be looked up in Django's [documentation]('https://docs.djangoproject.com/en/4.0/ref/models/fields/#foreignkey').

### [Modify Views]

The only thing we need to see are tasks assigned to the logged-in user. We need to hide the other tasks away. To do this, we can use the built in Django *filter* functionality.

{{< code-action >}} **Let's open `views.py`** Modify and add a few lines of code to the  `TaskDashboard`  and the `TaskForm` view.

```python {hl_lines=["11-13"]}
class TaskDashboard(ListView):
  template_name = 'starter_app/dashboard.html'
  model = Task

  def get_context_data(self, **kwargs):
      context = super().get_context_data(**kwargs)

      # filter out archieved tasks
      data = self.model.objects.all().filter(archive=False)

      # filter tasks for user and order by due date
      user_tasks = data.filter(task_user=self.request.user)
      context['user_tasks'] = user_tasks.distinct().order_by('-due_date')

      return context

```

Let's examine this code:
- The data.filter line of code will filter all the tasks that are for the user that is in self.request (aka, the user currently logged in).
- The context (or the user's tasks) will be sorted by due_date and this is what will be seen in the web page.


```python {hl_lines=["7"]}
class TaskForm(LoginRequiredMixin,FormView):
    template_name = 'task/TaskForm.html'
    form_class = TaskForm
    success_url = '/dashboard'

    def form_valid(self, form):
        form.instance.task_user = self.request.user
        form.save()
        return super().form_valid(form)
```

This addition will enable the form to automatically associate the new task with the current user.

Excellent! All the file changes have been made. We can migrate the changes on the database.

### [Run Migrations and Restart]

{{< code-action >}} **Remigrate the model so the changes you've made are reflected in the database.** To migrate, shut down the server, run the makemigrations and migrate commands, and restart the server.

```shell
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py runserver
```

After we run the migration, that Task table will be updated.

{{< code-action >}} **Let's test it and see if the web app now works as we expect!** Log in and add a new task. Check that the following changes have been made:
- Users can only create tasks for themselves
- Users can only view tasks they created


### [Resetting the Database]

When we test code and make a lot of edits to our database, we will be adding data at different database migration points. If we do this, there will be a high chance that we will add erroneous data that will no longer be consistent with whatever the current database architecture is.

If things get too messy, we would want to delete the database, delete our migrations and start fresh.

Here's how we do this.

0. Stop the server
1. Delete our database file. (/cs10_webapp_base/db.sqlite3)
2. Delete everything in the /starter_app/migrations folder. **Do not delete the folder!**
3. Run migrate to rebuild the database
4. Create a superuser
5. Restart the server

Performing these steps will reset our database with one superuser. With the superuser, we can access the admin page.

## [C] Expanding the Relation

We've now created a perfectly functioning personal to-do app!

What if we wanted to expand this app to work collaboratively?

A collaborative to-do app would allow individuals to assign tasks to other users. Powerschool has functionality similar to this. Teachers can assign homework, or tasks, to students.

We must account for the following use cases to implement this feature:
1. User can create a task for themselves
2. User can optionally create a task for others
3. Users can update a task they've created for others
3. User can view tasks for themselves
4. Users can view tasks they've assigned to others

{{< write-action >}} **In your notebook, think through what adjustments need to made to the model to create a collaborative to-do app.** Which other files will need adjustment? Once you have an outline of the changes, show a teacher before beginning to implement it.

{{< code-action >}} **Try to implement the features you outlined in the backend of the To-Do web app!**

<!-- ## [D] Conclusion

We have created a link or relation between the User table and Task table. We can use this relation to assigns tasks to different users in our To-Do app making our app work in a multi-user environment.

We have learned to update Django models, forms and views to take advantage of relational databases so that users can assign tasks to others.

With this basic understanding of how tables are joined in Django, we have opened up many more opportunities where we can have more than one-to-one relationships but also one-to-many and many-to-many relationships, similar to many real world apps.

The scope of this project is limited, but the sky's the limit in terms of what Django can do. You can do so much with Django and relational databases. What we have learned in these 5 mini-lessons is literally the tip of the iceberg. If you think about it, Instagram was made with Django so the possibilities are endless. -->
