## Ternary Operators

Ternary operators are more commonly known as conditional expressions in Python. These operators evaluate something based on a condition being true or not. They became a part of Python in version 2.4

Here is a blueprint and an example of using these conditional expressions.

__Blueprint__
```python
condition_is_true if condition_true else condition_is_false
```
__Example__
```python
is_fat = True
state = "fat" if is_fat else "not fat"
```
It allows to quickly test a condition instead of a multiline if statement.