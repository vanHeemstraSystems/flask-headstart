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
def index():
  return "Hello, World!"
  
if __name__ == "__main__":
    app.run(debug=True)
```

Try the basic app.py as follows.

From a terminal, run the following command:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
(env) [cloud_user@wvanheemstra2c flask-headstart]$  python3 
```

