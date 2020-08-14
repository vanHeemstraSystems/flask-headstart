... breadcrumbs ...

# 500 Create a Basic CRUD Application

## 510 Create

Video at 20:36 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Update 'templates/index.html' file as follows:

```
...
{% block body %}
<div class="content">
  <h1>Task Master</h1>
  <h2>Tasks</h2>
  <table>
    <tr>
      <th>Task</th>
      <th colspan="2">Added</th>
      <th>Actions</th>
    </tr>
    <tr>
      <td></td>
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

Video at 25:34 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

We are going to update the default route again in app.py:

```
...
@app.route('/', methods=['POST','GET'])
def index():
  if request.method == 'POST':
    return "Hello, World!"
  else:
    return render_template('index.html')
...
```

If we now submit the form, the page will be returned with a message

```
Hello, World!
```

Video at 26;27 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Instead, let us put in the logic for handling the form, so in app.py do:

```
...
@app.route('/', methods=['POST','GET'])
def index():
  if request.method == 'POST':
    task_content = request.form['content']
    new_task = Todo(content=task_content)
    
    try:
      db.session.add(new_task)
      db.session.commit()
      return redirect('/')
      
    except:
      return 'There was an issue with adding your task."
      
  else:
    tasks = Todo.query.order_by(Todo.date_created).all()
    return render_template('index.html', tasks=tasks)
...
```

## 520 Read

Video at 29:20 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

We need to update our templates/index.html for showing the tasks:

```
...
  {% for task in tasks %}
    <tr>
      <td>{{ task.content }}</td>
      <td>{{ task.date_created.date() }}</td>
      <td>{{ task.date_created.strftime('%X') }}</td>
      <td>
        ... leave what was already here ...
      </td>
    </tr>
  {% endfor %}  
...
```

Video at 31:14 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

We'll beautify our index page layout even more by the following added css in main.css.

```
body, html {
    margin: 0;
    font-family: sans-serif;
}
#background {
    background: url(../img/blueprint-background-11834.jpeg);
    background-repeat: no-repeat;
    background-size: auto;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    text-align: center;
    margin: 0;
    z-index: 999;
}
.content {
    border-radius: 5px;
    background:rgba(255, 255, 255, 0.6);
    margin: auto;
    margin-top: 20px;
    width: 800px;
}

table, td, th {
    border: 1px solid #aaa;
}

table {
    border-collapse: collapse;
    width: 100%;
}

th {
    height: 30px;
}

td {
    text-align: center;
    padding: 5px;   
}

.form {
    margin-top: 20px;
}

#content {
    width: 70%;
}
```

And center title of the table in index.html as follows:

```
...
<h1 style="text-align: center">Task Master</h1>
<h2 style="text-align: center">Tasks</h2>
...
```

## 530 Delete

Video at 31:18 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Add a route for deleting a Task in app.py as follows:

```
...

@app.route('/delete/<int:id>')
def delete(id):
  task_to_delete = Todo.query.get_or_404(id)
    
  try:
    db.session.delete(task_to_delete)
    db.session.commit()
    return redirect('/')
  except:
    return 'There was a problem deleting that task'
...
```

In addition, update the index.html so the Delet function will be triggered:

```
...
<td>
  <a href="/delete/{{task.id}}">Delete</a>
  ... leave what is already there
</td>
...
```

## 540 Update

Video at 34:06 youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Add the Update functionality to app.py as follows:

```
...
@app.route('/update/<int:id>', methods=['GET','POST'])
def update(id):
  task = Todo.query.get_or_404(id)
  
  if request.method == 'POST':
    task.content = request.form['content']
    
    try:
      db.session.commit()
      return redirect('/')
    except:
      return 'There was a problem updating that task.'
  else:
    return render_template('update.html', task=task)
...
```

Implement the Update function in templates/index.html as well.
```
...
<td>
  ... leave what was already here
  <a href="/update/{{task.id}}">Update</a>
</td>  
...
```

In addition, we require a new web page for updating, called update.html

```
cd templates
touch update.html
```

Add the following content to this update.html page:

```
{% extends 'base.html' %}

{% block head %}
<title>Task Master</title>
{% endblock %}

{% block body %}
<div id="background">
  <div class="content">
    <h1 style="text-align: center">Task Master</h1>
    <h2 style="text-align: center">Update Task</h2>
    <div class="form">
      <form action="/update/{{task.id}}" method="POST">
        <input type="text" name="content" id="content" value="{{task.content}}">
        <input type="submit" value="Update Task">
      </form>
    </div> 
  </div>
</div>
{% endblock %}
```

Video at 40:24 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Finally, in case there are no tasks at all, we will show a message instead of the table, like so in index.html:

```
...
{% if tasks|length < 1 %}
<h4 style="text-align:center">There are no tasks, create one below.</h4>
{% else %}

 ... leave what is already there, such as the table
 
{% endif %} 
...

```

## 550 EXTRA Styling

Based on "Blueprint Wireframes" at https://github.com/willem-vanheemstrasystems/blueprint-wireframes a responsive design.

We update the html, js, and css so it mimics the Blueprint Wireframe for a more enjoyable design.


The adjusted templates/index.html:
```

```

The adjusted templates/base.html:
```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=1">
        <meta http-equiv="X-UA-Compatible" content="ie-edge">
        <link rel="stylesheet" href="{{ url_for('static', filename='css/main.css') }}">
        <link rel="stylesheet" href="{{ url_for('static', filename='css/blueprint-wireframes/blueprint-wireframes.css') }}">
        <link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}">
        {% block head %}{% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
        
        <script type="text/javascript" src="{{ url_for('static', filename='js/main.js') }}"></script>
        <script type="text/javascript" src="{{ url_for('static', filename='js/jquery.js') }}"></script>
        <script type="text/javascript" src="{{ url_for('static', filename='js/easyModal.js') }}"></script>
        <script type="text/javascript" src="{{ url_for('static', filename='js/scripts.js') }}"></script>
    </body>
</html>
```

The adjusted templates/update.html:
```

```

The adjusted css/main.css:
```

```

The css/styles.css
```
/*
 * Apply your individual content reference wireframe styles here
 */

.header-main {
	position: relative;
	height: 55%;
	min-height: 22em;
	margin-top: 0;
}

.nav-main {
	height: 4em;
	width: 50%;
	max-width: 45em;
	position: absolute;
	top: 2%;
	right: 2%;

}

.nav-meta {
	clear: both;
	min-height: 1em;
	margin-top: 1em;
}

.logo {
	position: absolute;
	top: 2%;
	left: 2%;
	height: 4em;
	width: 13em;
	background: #fff;
}

.inner {
	max-width: 62.5em;
}

.in-header {
	position: absolute;
	top: 25%
}

.teaser-1,
.teaser-2,
.teaser-3 {
	float: left;
	width: 32%;
	margin-left: 2%;
	height: 8em;
	background: #5b79b9;
}

.teaser-1 {
	margin-left: 0;
}

.contact-block {
	margin-top: 1em;
}

.contact,
.socialmedia {
	float: left;
	width: 49%;
	margin-left: 2%;
	min-height: 8em;
	background: #5b79b9;
}

.contact {
	margin-left: 0;
}

.header-main .inner {
	position: absolute;
	bottom: 1em;
	left: 50%;
	margin-left: -500px;
}

.intro {
	margin: 2em auto;
}

.hint-welcome {
	width: 50%;
	height: auto;
}

@media (max-width: 37.5em) {

	.logo {
		margin: 0;
		width: 100%;
		position: relative;
		top: auto;
		left: auto;
	}

	.header-main {
		height: auto;
		min-height: 36em;
	}

	.nav-main {
		position: relative;
		width: 100%;
		top: auto;
		left: auto;
		right: auto;
		margin: 1em 0 8em;
	}

	.header-main .inner {
		position: relative;
		width: 100%;
		left: auto;
		right: auto;
	}

	.contact,
	.socialmedia {
		float: none;
		width: 100%;
		margin-left: 0;
		margin-bottom: 2%;
	}

	.teaser-1,
	.teaser-2,
	.teaser-3 {
		float: none;
		width: 100%;
		margin-left: 0;
		margin-bottom: 2%;
	}

	.teaser-3 {
		margin-bottom: 0;

	}
}

@media (max-width: 62.75em) {
	.header-main .inner {
		left: 1%;
		right: 1%;
		margin-left: 0;
		width: 98%;
	}
}
```

The css/blueprint-wireframes/blueprint-wireframe.css
```

```

The javascript js/jquery.js
```

```

The javascript js/easyModal.js
```

```

The javascript js/scripts.js
```

```
