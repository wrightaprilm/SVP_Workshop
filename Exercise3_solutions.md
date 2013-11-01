###Exercise 3 answer doc:

```python
>>> f_name = ['a','p','r','i','l']
>>> l_name = ['w','r','i','g','h','t']
>>> unique_to_f = []
>>> both = []
>>> for letter in f_name:
...     if letter in l_name:
...             both.append(letter)
...     elif letter not in l_name:
...             unique_to_f.append(letter)
... 
>>> both
['r', 'i']
>>> unique_to_f
['a', 'p', 'l']
```
Note that we could simplify this to:
```python
>>> for letter in f_name:
...     if letter in l_name:
...             both.append(letter)
...     else:
...             unique_to_f.append(letter)
```
Since there is only one "else" condition.

Your classmate came up with a clever solution for getting three lists, one which also has the letters that are uniqe to the last name.
```python
>>> for letter in f_name:
...     if letter in l_name:
...             both.append(letter)
...     else:
...             unique_to_f.append(letter)
>>>for letter in l_name:
...     if letter in both:
...             pass
...     else:
...             unique_to_l.append(letter)
>>> unique_to_l
['w', 'g', 'h', 't']
>>> both
['r', 'i']
>>> unique_to_f
['a', 'p', 'l']
```
 We can also use what are called 'list comprehensions':
 ```python
 >>> unique_l = [letter for letter in l_name if letter not in f_name]
>>> unique_l
['w', 'g', 'h', 't']
>>> unique_f = [letter for letter in f_name if letter not in l_name]
>>> unique_f
['a', 'p', 'l']
>>> both = [letter for letter in f_name if letter in l_name]
>>> both
['r', 'i']
```
Which are able to define and create lists at the same time!
