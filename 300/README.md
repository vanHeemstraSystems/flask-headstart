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

