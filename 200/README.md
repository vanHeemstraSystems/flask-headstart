.. add breadcrumbs ..

# 200 Get a Basic App Running

In Visual Studio Code, create a new file called '*app.py*' in the root directory of 'flask-headstart' if it is not already there.

``` 
[cloud_user@wvanheemstra2c flask-headstart] touch app.py
```

Now add the following code to '*app.py*':

```
from flask import Flask

app = Flask(__name__)

@app.route('/')


```


