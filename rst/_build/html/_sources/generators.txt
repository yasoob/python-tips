Generators
----------

Generators are iterators, but you can only iterate over them once. It’s
because they do not store all the values in memory, they generate the
values on the fly. You use them by iterating over them, either
explicitly with 'for' or implicitly by passing it to any function or
construct that iterates. Most of the time ``generators`` are implemented
as functions. However, they do not ``return`` a value, they ``yield``
it. Here is a simple example of a ``generator`` function:

.. code:: python

    def generator_function():
        yield 1
        yield 2
        yield 3

    for item in generator_function():
        print(item)
        
    # Output: 1
    # 2
    # 3

It is not really useful in this case. Generators are best for
calculating large sets of results (particularly calculations involving
loops themselves) where you don't want to allocate the memory for all
results at the same time. Python modified a lot of Python 2 functions
which returned ``lists`` to return ``generators`` in Python 3. It is
because ``generators`` are not resource intensive. Here is an example
which calculates fibonacci numbers:

.. code:: python

    # generator version
    def fibon(n):
        a = b = 1
        for i in xrange(n):
            yield a
            a, b = b, a + b

Now we can use it like this:

.. code:: python

    for x in fibon(1000000):
        print(x)

This way we would not have to worry about it using a lot of resources.
However, if we would have implemented it like this:

.. code:: python

    def fibon(n):
        a = b = 1
        result = []
        for i in xrange(n):
            result.append(a)
            a, b = b, a + b
        return result

It would have used up all our resources while calculating a large input.
Make sure that you follow this pattern and use ``generators`` whenever
they make sense. You wont be disappointed!
