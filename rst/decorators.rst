Decorators
----------

Decorators are a significant part of Python. In simple words they are
functions which modify the functionality of another function. They help
to make our code shorter and more Pythonic. Most of the beginners do not
know where to use them so I am going to share some areas where
decorators can make your code consise.

**Blueprint :**

.. code:: python

    from functools import wraps
    def decorator_name(f):
        @wraps(f)
        def decorated(*args, **kwargs):
            if not can_run:
                return "Function will not run"
            return f(*args, **kwargs)
        return decorated

    @decorator_name
    def func():
        print "Function is running"

    can_run = True
    print(func())
    # Output: Function is running

    can_run=False
    print(func())
    # Output: Function will not run

Note: ``@wraps`` takes a function to be decorated and adds the
functionality of copying over the function name, docstring, arguments
list, etc. This allows to access the pre-decorated function's properties
in the decorator.

Authorization
~~~~~~~~~~~~~

Decorators can help to check whether someone is authorized to use an
endpoint in a web application. They are extensively used in Flask web
framework and Django. Here is an example to employ decorator based
authentication:

**Example :**

.. code:: python

    from functools import wraps

    def requires_auth(f):
        @wraps(f)
        def decorated(*args, **kwargs):
            auth = request.authorization
            if not auth or not check_auth(auth.username, auth.password):
                return authenticate()
            return f(*args, **kwargs)
        return decorated

Logging
~~~~~~~

Logging is another area where the decorators shine. Here is an example:

.. code:: python

    from functools import wraps

    def logit(func):
        @wraps(func)
        def with_logging(*args, **kwargs):
            print func.__name__ + " was called"
            return func(*args, **kwargs)
        return with_logging

    @logit
    def addition_func(x):
       """does some math"""
       return x + x


    result = addition_func(4)
    # Output: addition_func was called

I am sure you are already thinking about some clever uses of decorators.
