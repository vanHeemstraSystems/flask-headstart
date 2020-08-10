... breadcrumbs ...

# 400 Setting Up and Using Database (SQLite)

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
app.config['SQLACHEMY_DATABASE_URI'] = 'sqlite:///test.db' # relative path
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

Lastly, we will have to create the test.db file in the root directory

```
touch test.db
```

