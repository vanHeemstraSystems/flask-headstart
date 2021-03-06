... breadcrumbs ...

# 400 Setting Up and Using Database (SQLite)

Preparations:

First, install these modules:
```
pip install pylint-flask
pip install pylint-flask-sqlalchemy
```
Then, in Visual Studio Code, you need to add the following to your settings.json file:

```
"python.linting.pylintArgs": ["--load-plugins", "pylint-flask", "pylint-flask-sqlalchemy"]
```

TIP: If it doesn't seem to take effect, try reloading Visual Studio Code (Command Palette > Developer > Reload Window). Source https://stackoverflow.com/questions/53975234/instance-of-sqlalchemy-has-no-column-member-no-member

Video at 15:40 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Import SQLAlchemy (and datetime, which will be used in the Model later on) in the top part of app.py as follows:

```
...
from flask_sqlalchemy import SQLAlchemy
from datetime import datetime
...
```

In addition, add the database settings to app.py as follows:

```
...
# database settings
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///test.db' # relative path
db = SQLAlchemy(app)
...
# database model
class Todo(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    content = db.Column(db.String(200), nullable=False)
    date_created = db.Column(db.DateTime, default=datetime.utcnow)
    
    def __repr__(self):
        return '<Task %r>' % self.id    
...
```

Next we need to creatre the database based on the configuration in app.py.

We do so by going into the interactive mode of Python3 shell by typing:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
(env) [cloud_user@wvanheemstra2c flask-headstart]$  python3
>>> from app import db
```

Followed by:

```
>>> db.create_all()
```

The above should create a database.

Video at 20:29 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Lastly, we will see that the test.db file has been created in the root directory

```
test.db
```

