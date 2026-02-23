---
Title: "[1. Views]"
# draft: True

---

# Views

**Views** are the key link between the `Model` and `HTML` files. Django has two main types of views:
- [class based views](https://docs.djangoproject.com/en/4.1/topics/class-based-views/)
- [function based views ](https://docs.djangoproject.com/en/4.1/topics/http/views/)

---

## [1] Class Base Views


{{< look-action >}} **Let's start by looking at our existing class based views in `ridde_app/views.py`** Each view inherits a Django view. For now we are going to ignore `NewRiddleForm(FormView)`. We will go in-depth in `forms` in a later lab.
- `IndexView(TemplateView)`
- `RiddleListView(ListView)`
- `RiddleDetailView(DetailView)`

📖 **Take a look at documentation for each Class View**
- [`TemplateView`](https://docs.djangoproject.com/en/4.1/ref/class-based-views/base/#templateview)
- [`ListView`](https://docs.djangoproject.com/en/4.1/ref/class-based-views/generic-display/#listview)
- [`DetailView`](https://docs.djangoproject.com/en/4.1/ref/class-based-views/generic-display/#detailview)

There are a TON of different ways to achieve the same outcome in Django. We will just explore a few of them in this lab. 

---

### [TemplateView]

**`TemplateView` is a view that simply directs the a `url path` to a `HTML` file.** 

{{< look-action >}} **Let's look at `IndexView(TemplateView)`.** You can view it [HERE](http://127.0.0.1:8000/).
```python
class IndexView(TemplateView):
    template_name = "index.html"
```
> The only **attribute `TemplateView` NEEDS** is  a `template_name`. 

☑️ **Let's add complexity to our `IndexView` by having a random riddle appear on our index page.**

{{< code-action >}} **In `IndexView(TemplateView)` add the `get_context_data()` function.** This is a powerful function that allows you to send data to a template.
```python
def get_context_data(self, **kwargs):
    context = super().get_context_data(**kwargs)
    context['riddle'] = Riddle.objects.order_by("?").first()
    return context
```
> *`order_by("?")` can be slow with larger databases, you can read more about it [here](https://stackoverflow.com/questions/71372183/django-get-random-object-from-database-by-id-but-if-id-doesnt-exist-try-again) if interested*


{{< code-action >}} **To see the random riddle appear, you will need to use the `context['riddle']` in `templates/index.html`.** Add the line below to `line 8`.
```html
{{riddle}}
```

🧐 **You may be wondering, why does it show the question?** That is because the `__str__()` method is overridden in `ridde_app/models.py`. 
```python
def __str__(self):
    return f"{self.question}"
```

{{< code-action >}} **Add another `Riddle` property to the `__str()` method.**

🌐 **Refresh [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to see your changes!**

{{< code-action >}} **Now, return to the `index.html` page and try just showing the riddle answer, by using the fields.**
```html
{{riddle.answer}}
```

There are multiple ways to have control over what appears in the template! 

---

**Context Data is a very powerful dictionary** that allows you to send data to your template! You can add as many key, value pairs the `context` as you need. 

```python
context = {
    'riddle': Riddle.objects.order_by("?").first()
}
```

{{< code-action >}} **Try, adding a new `key`,`value` pair and see if you can access it in `index.html`** 

{{< expand "Example get_context_data() ">}}
```python
def get_context_data(self, **kwargs):
    context = super().get_context_data(**kwargs)
    context['riddle'] = Riddle.objects.order_by("?").first()
    context['message'] = "hello world"
    return context
```

{{< /expand >}}

---

### [ListView]

`ListView` is a view that sends an entire `Queryset` of a model. You can think of a `Queryset` as a list of models.

{{< look-action >}} **Let's look at `RiddleList(TemplateView)`.** 
```python
class RiddleListView(ListView):
    model = Riddle
    template_name = "riddle_list.html"

    queryset = Riddle.objects.all()
```
> - it requires you to specify a `model` and a `template_name`
> - by defining a `queryset` you can have more control over what data gets sent

{{< code-action >}} **Use `.order_by()` to change the sort order of riddles.** Up to you to decide how to sort.
```shell
>>> Riddle.objects.order_by('likes')
<QuerySet [<Riddle: Where does today come before yesterday?>, <Riddle: I speak without a mouth and hear without ears. I have no body, but I come alive with wind. What am I?>, <Riddle: who am i?>, <Riddle: What is black when it’s clean and white when it’s dirty?>, <Riddle: I’m the rare case when today comes before yesterday. What am I?>]>
>>>  Riddle.objects.order_by('question')
<QuerySet [<Riddle: I speak without a mouth and hear without ears. I have no body, but I come alive with wind. What am I?>, <Riddle: I’m the rare case when today comes before yesterday. What am I?>, <Riddle: What is black when it’s clean and white when it’s dirty?>, <Riddle: Where does today come before yesterday?>, <Riddle: who am i?>]>
>>>   Riddle.objects.order_by('-question')
<QuerySet [<Riddle: who am i?>, <Riddle: Where does today come before yesterday?>, <Riddle: What is black when it’s clean and white when it’s dirty?>, <Riddle: I’m the rare case when today comes before yesterday. What am I?>, <Riddle: I speak without a mouth and hear without ears. I have no body, but I come alive with wind. What am I?>]>
```
> - what is the difference between `('question')` and `('-question')`?

🌐 **Refresh and visit [127.0.0.1:8000/riddle/list](http://127.0.0.1:8000/riddle/list) to see your changes!** 

---

**You can also add the `get_context_data()` method into a `ListView`.**

{{< code-action >}} **Add the `get_context_data()` method to `RiddleList(TemplateView)`** 
- Send data to communicate what how the riddles are sorted
- Display the data on the `riddle_list.html` page. 

{{< expand "Example riddle_list.html">}}
```html
<h1>All Riddles sorted by {{ order_by }}</h1>

```

{{< /expand >}}

---

### [DetailView]

`DetailView` is a view that sends **one** instance of a model. In this app, it will send one `Riddle` object. 


{{< look-action >}} **Let's look at `RiddleDetailView(DetailView)`.** 
```python
class RiddleDetailView(DetailView):
    model = Riddle
    template_name = "riddle_detail.html"

```
> - it requires you to specify a `model` and a `template_name`

{{< look-action >}} **Now, let's take a look at `line 9` in `riddle_app/urls.py`.** 
```python
path('riddle/detail/<int:pk>/', RiddleDetailView.as_view(), name='riddle-detail'),
```
> **`<int:pk>`** - this tells the `DetailView` which `Riddle` to send based on the `id`

🌐 **Try it out by visiting the path [http://127.0.0.1:8000/riddle/detail/1](http://127.0.0.1:8000/riddle/detail/1).** You can change `1` to any `id` that is in the database.


---

**You can also add the `get_context_data()` method into a `DetailView`.**

{{< code-action >}} **Add the `get_context_data()` method to `RiddleDetailView(DetailView)` to send the current datetime the page is accessed.**  You will need to reference the resources to figure out how to do this.

- Send data to communicate what time the page was accessed 
- Display the data on the `riddle_detail.html` page. 
- Resources
    - [DetailView documentation](https://docs.djangoproject.com/en/4.1/ref/class-based-views/generic-display/#detailview)
    - [datetime documentation](https://docs.djangoproject.com/en/4.1/topics/i18n/timezones/)

🌐 **Test your changes by visiting the path [127.0.0.1:8000/riddle/detail/1](http://127.0.0.1:8000/riddle/detail/1).** 

---

## [2] Function Views

Function based views are great for when a class based view does not fit your needs or if you want more specific over the `GET` and `POST` request cycle. In this app we function based views for:
- liking a riddle
- guessing a riddle

{{< code-action >}} **Add a dislike feature to your app that simply the `likes`.** You will need to edit:
- `riddle_app/models.py`
- `riddle_app/views.py`
- `riddle_app/urls.py`
- `riddle_app/templates/riddle_detail.html`

🌐 **Test your changes by visiting the path [127.0.0.1:8000/riddle/detail/1](http://127.0.0.1:8000/riddle/detail/1).** 


---

## [3] Deliverables 

{{< deliverables >}}
{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}


---

## [Extension]

Try implementing any of these features:
- a new `ListView` to only see easy, medium, or hard riddles
- a [`UpdateView`](https://docs.djangoproject.com/en/4.1/ref/class-based-views/generic-editing/#django.views.generic.edit.UpdateView) - to allow a user to change an existing `Riddle`
- a non-destructive way to 'delete' riddles by 'archiving' them

