##Decorators

Decorators are a significant part of Python. In simple words they are functions which modify the functionality of another function. They help to make our code shorter and more Pythonic. Most of the beginners do not know where to use them so I am going to share some areas where decorators can make your code consise.

__Blueprint :__

```python
def decorator_name(f):
    def decorate(*args, **kwargs):
        if not can_run:
            return "Kindly authenticate"
        return f(*args, **kwargs)
    return decorated

@decorator_name
def func():
    print "lola"

can_run = True
print func()

can_run=False
func()
```

###Authorization

Decorators can help to check whether someone is authorized to use an endpoint in a web application. They are extensively used in Flask web framework and Django. Here is an example to employ decorator based authentication:

__Example :__

```python
from functools import wraps

def requires_auth(f):
    # @wraps
    @wraps(f)
    def decorated(*args, **kwargs):
        auth = request.authorization
        if not auth or not check_auth(auth.username, auth.password):
            return authenticate()
        return f(*args, **kwargs)
    return decorated
```

###Logging

Logging is another area where the decorators shine. Here is an example:

```python
from functools import wraps
def logged(func):
    @wraps(func)
    def with_logging(*args, **kwargs):
        print func.__name__ + " was called"
        return func(*args, **kwargs)
    return with_logging

@logged
def f(x):
   """does some math"""
   return x + x * x

print f.__name__  # prints 'f'
print f.__doc__   # prints 'does some math'
```