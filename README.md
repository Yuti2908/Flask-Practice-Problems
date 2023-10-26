# Flask-Practice-Problems
Few practice problems based on Flask


## Problem 1:

```
from flask import Flask
app=Flask(__name__)

@app.route("/")
def hello_world():
    return "Hello World"

if __name__=="__main__":
    app.run()
```

## Problem 2:

```
from flask import Flask
app=Flask(__name__)

@app.route("/hello/<name>")
def hello_name(name):
    return "Hello %s!" %name

@app.route("/")
def hello():
    return "Hello World"

if __name__=="__main__":
    app.run()
```

## Problem 3:

```
from flask import Flask
app=Flask(__name__)

@app.route("/blog/<int:postID>")
def show_blog(postID):
    return 'Blog number is %s' %postID

@app.route("/rev/<float:revNo>")
def revision(revNo):
    return 'Revision number  is %s' %revNo

@app.route("/name/<usrName>")
def show_name(usrName):
    return "User name given is: %s" %usrName

@app.route("/")
def hello():
    return "Hello World"


if __name__=="__main__":
    app.run()
```

## Problem 4:

```
from flask import Flask
app = Flask(__name__)

@app.route("/admin")
def hello_admin():
    return 'Hello Admin Sir!!'

@app.route("/guest/<guest>")
def hello_guest(guest):
    return "hello %s you logged in as guest user" % guest

@app.route("/usr/<name>")
def hello_user(name):
    if name == 'admin':
        return redirect(url_for('hello_admin'))
    else:
        return redirect(url_for('hello_guest',guest=name))

if __name__=='__main__':
    app.run(debug = True)
```

## Problem 5:

```
from flask import Flask
app=Flask(__name__)

@app.route("/success/<name>")
def success(name):
    return "Welcome Mr/Mrs. %s" %name

@app.route("/login", method = ["POST","GET"])
def login():
    if request.method == "POST":
        user=request.form("nm")
        return redirect(url_for('success',name = user))
    else:
        user=request.arg.get("nm")
        return redirect(url_for("success",name=user))

if __name__=="__main__":
    app.run()
```

### login.html

```
<!DOCTYPE html>
<html lang="en">
<body>
<form action="http://localhost:5000/login" method = "post">
    <p>Enter name</p>
    <p><input type ="text" name="nm"</p>
    <p><input type="submit" value = "submit"</p>
</form>

</body>
</html>
```

## Problem 6:

```
from flask import Flask
from flask import render_template
app = Flask(__name__)

@app.route("/hello/<user>")
def hello_name(user):
    return render_template('hello.html', name = user)

if __name__=="__main__":
    app.run(debug=True)
```

### hello.html

```
<!DOCTYPE html>
<html lang="en">

<body>
<h1>Hello Mr/Mrs. {{ name }}</h1>

</body>
</html>
```
