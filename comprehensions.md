## Comprehensions

Comprehensions are a feature of Python which I would really miss if I ever have to leave it. Comprehensions are constructs that allow sequences to be built from other sequences. There are three type of comprehensions in Python:

- list comprehensions
- dictionary comprehensions
- set comprehensions

`list` comprehensions were introduced in Python 2. `set` and `dictionary` comprehensions became a part of Python in version 3.0.

We will discuss them one by one. Once you get the hang of using `list` comprehensions then you can use anyone of them easily.

####`list` comprehensions

List comprehensions provide a short and concise way to create lists. It consists of square brackets containing an expression followed by a `for` clause, then zero or more `for` or `if` clauses. The expressions can be anything, meaning you can put in all kinds of objects in lists. The result would be a new list made after the evaluation of the expression in context of the `if` and `for` clauses.

Here is a short example:

```python
multiples = [i for i in range(30) if i % 3 is 0]
print(multiples)
# Output: [0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
```

This can be really useful to make lists quickly. It is even preferred by some instead of `filter` function. `list` comprehensions are more useful when you want to supply a list to a method or function to make a new list.

```python
L = []
for x in range(10):
    L.append(x**2)
```