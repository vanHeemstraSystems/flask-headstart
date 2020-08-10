... breadcrumbs ...

# 300 Templates and Static Content


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

Activate the virtual environment as follows:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
```

Then start the application:

```
(env) [cloud_user@wvanheemstra2c flask-headstart]$ python3 app.py
```

When you open your browser at localhost:5000 you should see:

```
Hello, World! 2
```

It is now showing the index.html file instead of the text "Hello, World!" by itself.




