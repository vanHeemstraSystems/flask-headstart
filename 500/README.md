... breadcrumbs ...

# 500 Create a Basic CRUD Application

Video at 20:36 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Update 'templates/index.html' file as follows:

```
...
{% block body %}
<div class="content">
  <h1>Task Master</h1>
  <table>
    <tr>
      <th>Task</th>
      <th>Added</th>
      <th>Actions</th>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>
        <a href="">Delete</a>
        <br>
        <a href="">Update</a>
      </td>
    </tr>
  </table>
</div>
{% endblock %}
...

```

Video at 22:39 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Update the default route in app.py with some methods, as follows:

```
...
@app.route('/', methods=['POST','GET'])
def index():
  return render_template('index.html')
...

```

Now we are able to handel POST requests (for a filled in form for example) as well as GET requests (for a page for example).

Video at 23:00 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Let's create the form to add a new Task.

In templates/index.html add the following below the already existing table, but inside the div of "contents":

```
...
<form action="/" method="POST">
  <input type="text" name="content" id="content">
  <input type="submit" value="Add Task">
</form>
...

```

Video at 24:01 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Now add a title to the default page, templates/index.html:

```
...
{% block head %}
<title>Task Master</title>
{% endblock %}
...
```

Video at 25:01 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

We are going to update the default route again in app.py:

```
...
@app.route('/', methods=['POST','GET'])
def index():

...
```


