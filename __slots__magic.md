## \_\_slots\_\_ Magic

By default Python uses a dict to store an object’s instance attributes. This is really helpfulas it allows setting arbitrary new attributes at runtime. 

However, in small classes with known attributes it might be a bottleneck. Python can’t just allocate a static amount of memory at object creation to store all the attributes. Therefore it sucks a lot of RAM if you create a lot of classes (I am talking in thousands and millions). Still there is a way to circumvent this issue. It involves the useage of `__slots__` to tell Python not to use a dict, and only allocate space for a fixed set of attributes. Here is an example with and without `__slots__`:

__Without__ `__slots__`

```python

```