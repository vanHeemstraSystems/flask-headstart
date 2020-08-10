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

Video at 08:48 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Try the basic app.py as follows.

From a terminal, run the following command from the root directory:

```
[cloud_user@wvanheemstra2c flask-headstart]$ source env/bin/activate
(env) [cloud_user@wvanheemstra2c flask-headstart]$  python3 app.py
```

This will start the local web server, listening on port 5000.

Open a browser and go to http://localhost:5000

You should see the following text on the web page:

```
Hello, World!
```


