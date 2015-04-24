##Decorators

Decorators are a significant part of Python. In simple words they are functions which modify the functionality of another function. They help to make our code shorter and more Pythonic. Most of the beginners do not know where to use them so I am going to share some areas where decorators can make your code consise.

###Authorization

Decorators can help to check whether someone is authorized to use an endpoint in a web application. They are extensively used in Flask web framework and Django. Here is an example to employ decorator based authentication:

__Blueprint :__

```python
def requires_auth(f):
    def decorated(*args, **kwargs):
        auth = authentication_data
        if not auth or not check_auth(auth):
            return "Kindly authenticate"
        return f(*args, **kwargs)
    return decorated
```
__Usage :__
