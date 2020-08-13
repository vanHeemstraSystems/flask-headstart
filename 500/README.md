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

***IMPORTANT***: Add the 'request' and 'redirect' to the import of app.py.

```
from flask import Flask, render_template, url_for, request, redirect
...
```

We are going to update the default route again in app.py:

```
...
@app.route('/', methods=['POST','GET'])
def index():
  if request.method == 'POST':
    apss
  else:
    pass

...
```

EXTRA: To set a nice background, do the following:

Upload a background image to a new folder called 'img' in 'static' folder:

NOTE: Background image comes from http://seekgif.com/free-image/circular-blueprint-background----11834.html

```
cd static
mkdir img
```

Next, update 'templates/index.html' so it can support a background image:

```
...
<div id="background">
  <div class="content">
     ... leave what was already there ...
  </div>
</div>
...
```

Then, add the following to 'static/css/main.css':

```
...
#background {
    background: url(../img/blueprint-background-11834.jpeg);
    background-repeat: no-repeat;
    background-size: auto;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    margin: 0;
    z-index: 999;
}
.content {
    background:rgba(255, 255, 255, 0.6);
    margin: 0;
}
...
```
