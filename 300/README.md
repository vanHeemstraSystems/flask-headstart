... breadcrumbs ...

# 300 Templates and Static Content

We are using ***Jinja2*** templating syntax, see also https://jinja.palletsprojects.com/en/2.11.x/templates/

Video at 08:56 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Create the following folder in the root of the repository for our static content:

```
mkdir static
```

Create the following folder in the root of the repository for our templates:

```
mkdir templates
```

In 'app.py' add render_template to the import statement as follows:

```
from flask import Flask, render_template
...
```

Inside the 'templates' folder, create a new file called 'index.html':

```
cd templates
touch index.html
```

NOTE: You could also create it from within Visual Studio Code.

Now inside 'app.py' replace the line 

```
return "Hello, World!"
```

by

```
return render_template('index.html')
```

Update 'templates/index.html' as follows:

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie-edge">
        <title>Document</title>
    </head>
    <body>
        Hello, World! 2
    </body>
</html>
```

Activate the virtual environment as follows, unless it was already activated:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
```

Then start the application, unless it was already started, as it will update the page automatically:

```
(env) [cloud_user@wvanheemstra2c flask-headstart]$ python3 app.py
```

When you open your browser (and refresh) at localhost:5000 you should see:

```
Hello, World! 2
```

It is now showing the index.html file instead of the text "Hello, World!" by itself.


## Template Inheritance

Video at 10:04 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Create a new file called "base.html" inside the templates folder:

```
cd templates
touch base.html
```

Update the file "base.html" as follows:

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie-edge">
        {% block head %}{% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
    </body>
</html>
```
Notice the above lines:

```
{% block head %}{% endblock %}
```
and
```
{% block body %}{% endblock %}
```

These are dynamic content placeholders, used by the template engine.

Video at 11:28 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

To make use of the template engine placeholders, update the 'templates/index.html' file as follows:

```
{% extends 'base.html' %}

{% block head %}

{% endblock %}

{% block body %}
<h1>Template</h1>
{% endblock %}
```

## Static Content

Video at 13:00 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Inside the 'static' folder, create a subfolder called 'css':

```
cd static
mkdir css
```

Inside the newly created folder 'css' create a file called 'main.css':

```
cd css
touch main.css
```

Now add the following to 'main.css' for styling purposes

```
body {
    margin: 0;
    font-family: sans-serif;
}
```

To add the reference to the main.css in the base.html, update the base.html as follows:

```
...
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie-edge">
        <link rel="stylesheet" href="{{ url_for('static', filename='css/main.css') }}">
        {% block head %}{% endblock %}
    </head>
...
```

Also import the 'url_for' in app.py:

```
from flask import Flask, render_template, url_for
...
```

Now refreshing your web page, the font of the text in the body will have become 'sans-serif', as specified in main.css.


