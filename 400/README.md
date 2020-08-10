... breadcrumbs ...

# 400 Setting Up and Using Database (SQLite)

Video at 15:40 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Import SQLAlchemy in the top part of app.py as follows:

```
...
from flask_sqlalchemy import SQLAlchemy
...
```

In addition, add the database settings to app.py as follows:

```
...
# database settings
app.config['SQLACHEMY_DATABASE_URI'] = 'sqlite:///test.db' # relative path
db = SQLAlchemy(app)
...
```

Lastly, we will have to create the test.db file in the root directory

```
touch test.db
```

