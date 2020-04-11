# Python programming

Some of my notes related to the awesomeness that is the Python programming language.

Contents:

- [String](#string)
- [Dictionary](#dictionary)
- [List](#list)
- [Further Reading](#further-reading)

## String

A string in Python is represented by a series of characters enclosed by single or double quotes.

```python
# declare a string
s = 'hello there'
t = "yap, it's another string"
```

```python
# return a capitalized version of the string
>>> s = 'hello there'
>>> s.capitalize()
'Hello there'
```

```python
# return a caseless (un-capitalized) version of the string
>>> s = 'HeLlo TheRe'
>>> s.casefold()
'hello there'
```

## Dictionary

```python
d = {'one': 1, 'two': 2}
```

Update a dictionary with the key/value pairs from another dictionary. This overwrites existing keys in the original dictionary.

```python
params = {'d': 3.14, 'ep': 0.46, 'phi': 0.8}
case1 = {'d': 2.89, 'phi': 0.9}

params.update(case1)
# updates `params` to {'d': 2.89, 'ep': 0.46, 'phi': 0.9}
```

## List

```python
a = [1, 2, 3, 4]
```

## Enumerate and zip

Iterate over two lists along with their indices.

```python
x = ['apple', 'orange', 'melon', 'peach']
y = [3.4, 2.56, 5.10, 7.02]

for i, (x, y) in enumerate(zip(x, y)):
    print(i, x, y)
```

Prints the following:

```
0 apple 3.4
1 orange 2.56
2 melon 5.1
3 peach 7.02
```

## Further Reading

- [Python.org](https://www.python.org)
- [Real Python](https://realpython.com)
