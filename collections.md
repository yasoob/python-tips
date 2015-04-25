## Collections

Python ships with a module that contains a number of container data types called Collections. We will talk about a few of them and discuss their usefullness.

The ones which we will talk about are:

- `defaultdict`
- `counter`
- `deque`

####1.`defaultdict`

I personally use defaultdict quite a bit. Unlike `dict`, with `defaultdict` you do not need to check whether a key is present or not. So we can do:

```python
from collections import defaultdict
 
colours = (
    ('Yasoob', 'Yellow'),
    ('Ali', 'Blue'),
    ('Arham', 'Green'),
    ('Ali', 'Black'),
    ('Yasoob', 'Red'),
    ('Ahmed', 'Silver'),
)
 
favourite_colours = defaultdict(list)
 
for name, colour in order:
    favourite_colours[name].append(colour)
 
print(favourite_colours)
 
# output 
# defaultdict(<type 'list'>, 
#    {'Arham': ['Green'], 
#     'Yasoob': ['Yellow', 'Red'], 
#     'Ahmed': ['Silver'], 
#     'Ali': ['Blue', 'Black']
# })
```
We can also count the number of individual favourite colours:

```python
from collections import defaultdict
 
colours = (
    ('Yasoob', 'Yellow'),
    ('Ali', 'Blue'),
    ('Arham', 'Green'),
    ('Ali', 'Black'),
    ('Yasoob', 'Red'),
    ('Ahmed', 'Silver'),
)
 
favourite_colours = defaultdict(int)
 
for name, colour in colours:
    favourite_colours[name] += 1


print(favourite_colours)
# Output: defaultdict(<type 'int'>, {
#       'Arham': 1, 
#       'Yasoob': 2, 
#       'Ahmed': 1, 
#       'Ali': 2
# })
```

One another very important use case is when you are appending to ists inside a dictionary. If a `key` is not already present in the dictionary then you are greeted with a `KeyError`. `defaultdict` allows us to circumvent this issue in a neat way. First let me share an example using `dict` which raises `KeyError` and then I will share a solution using `defaultdict`.

__Problem:__

```python
some_dict = {}
some_dict['colours']['favourite'] = "yellow"
# Raises KeyError: 'colours'
```

__Solution:__

```python
import collections
tree = lambda: collections.defaultdict(tree)
some_dict = tree()
some_dict['colours']['favourite'] = "yellow"
# Works fine
```

You can print the `some_dict` using `json.dumps`. Here is some sample code:

```python
import json
print(json.dumps(some_dict))
# Output: {"colours": {"favourite": "yellow"}}
```

####2.`counter`

