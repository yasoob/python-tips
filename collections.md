## Collections

Python ships with a module that contains a number of container data types called Collections. We will talk about a few of them and discuss their usefullness.

The ones which we will talk about are:

- `defaultdict`
- `counter`
- `deque`
- `namedtuple`

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

One another very important use case is when you are appending to nested ists inside a dictionary. If a `key` is not already present in the dictionary then you are greeted with a `KeyError`. `defaultdict` allows us to circumvent this issue in a clever way. First let me share an example using `dict` which raises `KeyError` and then I will share a solution using `defaultdict`.

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

Counter allows us to count the occurances of a particular item. For instance it can be used to count the number of individual favourite colours:

```python
from collections import Counter
 
colours = (
    ('Yasoob', 'Yellow'),
    ('Ali', 'Blue'),
    ('Arham', 'Green'),
    ('Ali', 'Black'),
    ('Yasoob', 'Red'),
    ('Ahmed', 'Silver'),
)
 
favs = Counter(name for name, colour in colours)
print(favs)
# Output: Counter({
#    'Yasoob': 2, 
#    'Ali': 2, 
#    'Arham': 1, 
#    'Ahmed': 1
# })
```

We can also count the most common lines in a file using it. For example:

```python
with open('filename', 'rb') as f:
    line_count = Counter(f)
print(line_count)
```

####3.`deque`
`deque` provides you with a double ended queue which means that you can append and delete elements from either side of the queue. First of all you have to import the deque module from the collections library:

```python
from collections import deque
```

Now we can instantiate a deque object.

```python
d = deque()
```

It works like python lists and provides you with somewhat similar methods as well. For example you can do:

```python
d = deque()
d.append('1')
d.append('2')
d.append('3')

print(len(d))
# Output: 3

print(d[0])
# Output: '1'

print(d[-1])
# Output: '3'
```

You can pop values from both sides of the deque:

```python
d = deque([i for i in range(5)])
print(len(d))
# Output: 5

d.popleft()
# Output: 0

d.pop()
# Output: 4

print(d)
# Output: deque([1, 2, 3])
```

We can also limit the amount of items a deque can hold. By doing this when we achieve the maximum limit of out deque it will simply pop out the items from the opposite end. It is better to explain it using an example so here you go:

```python
d = deque(maxlen=30)
```

Now whenever you insert values after 30, the leftmost value will be popped from the list. You can also expand the list in any direction with new values:

```python
d = deque([1,2,3,4,5])
d.extendleft([0])
d.extend([6,7,8])
print(d)
# Output: deque([0, 1, 2, 3, 4, 5, 6, 7, 8])

```

This was just a quick drive through the `collections` module. Make sure you read the official documentation after reading this.

####4.`namedtuple`
It is essentially a tuple 
