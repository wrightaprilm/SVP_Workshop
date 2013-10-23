#Variables

Variables are names for objects that we'd like to store.

When we assign them, we use the 

```python
=
```

operator. When, for example, we type:

```python
>>> observations = 5
```

we set the value of observations to five. If we type:

```python
>>> print observations
```

we should receive

```
5
```

in response. 

```UNIX

**A note on names**

As scientists, we often want to be very explicit when recording information. This is good. But spaces in the name of a variable in Python, will cause the name to be read wrong. Observe:

```python
>>> number of observations = 5
      ^
SyntaxError: invalid syntax

```

Because of the space, Python has become confused about what you're assigning and to which variable. The error we received is a syntax error, which tells us that there is some problem with the way we've entered the command.
For best results, staying away from spaces in naming is a good idea.

```
