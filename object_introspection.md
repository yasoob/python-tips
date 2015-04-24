## Object introspection

In computer programming, introspection is the ability to determine the type of an object at runtime. It is one of Python's strengths. Everything in Python is an object and we can examine those objects. Python provides us with a few Built-in functions to help us.

####1. `dir()`

It is one of the most important functions for introspection. It returns a list of attributes and methods belonging to an object. Here is an example:

```python
my_list = [1, 2, 3]
dir(my_list)
# Output: ['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', 
# '__delslice__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', 
# '__getitem__', '__getslice__', '__gt__', '__hash__', '__iadd__', '__imul__', 
# '__init__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', 
# '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__',
# '__setattr__', '__setitem__', '__setslice__', '__sizeof__', '__str__', 
# '__subclasshook__', 'append', 'count', 'extend', 'index', 'insert', 'pop', 
# 'remove', 'reverse', 'sort']
```

Our introspection gave us the names of all the methods of a list. This can be handy when you are not able to recall a method name. If we run `dir()` without any argument then it returns all names in the current scope.

There are a couple of other methods as well which help in introspection. You can explore them if you wish.