---
title: Dive Into Python 3
name: dive-into-python-3
date: 2024-09-05
draft: false
tags:
  - CS
share: "true"
---

# 1. Your First Python Program
## 1.1. Diving In
```shell
$ python3 humansize.py
```
## 1.2. Declaring Functions
### 1.2.1. Optional and Named Arguments
```python
def approximate_size(size, a_kilobyte_is_1024_bytes=True):
```
## 1.3. Writing Readable Code
### 1.3.1. Documentation Strings
Triple quotes
```python
def approximate_size(size, a_kilobyte_is_1024_bytes=True):
    '''Convert a file size to human-readable form.


    Keyword arguments:
    size -- file size in bytes
    a_kilobyte_is_1024_bytes -- if True (default), use multiples of 1024
                                if False, use multiples of 1000

    Returns: string

    '''
```
## 1.4. The `import` Search Path
```python
>>> import sys
>>> sys.path
['', '/opt/homebrew/Cellar/python@3.11/3.11.6_1/Frameworks/Python.framework/Versions/3.11/lib/python311.zip', '/opt/homebrew/Cellar/python@3.11/3.11.6_1/Frameworks/Python.framework/Versions/3.11/lib/python3.11', '/opt/homebrew/Cellar/python@3.11/3.11.6_1/Frameworks/Python.framework/Versions/3.11/lib/python3.11/lib-dynload', '/Users/kagableed/Library/Python/3.11/lib/python/site-packages', '/opt/homebrew/lib/python3.11/site-packages']
>>>
```
## 1.5. Everything Is An Object
one of the function’s attributes, `__doc__`
```python
>>> import humansize
>>> print(humansize.approximate_size.__doc__)
Convert a file size to human-readable form.


    Keyword arguments:
    size -- file size in bytes
    a_kilobyte_is_1024_bytes -- if True (default), use multiples of 1024
                                if False, use multiples of 1000

    Returns: string

    
>>> 
```

### 1.5.1. What’s An Object?
In Python, functions are _first-class objects_. Modules are _first-class objects_. Classes are first-class objects, and individual instances of a class are also first-class objects.
_everything in Python is an object_. Strings are objects. Lists are objects. Functions are objects. Classes are objects. Class instances are objects. Even modules are objects.

## 1.6. Indenting Code
Indentation is a language requirement and not a matter of style.
Python uses carriage returns to separate statements and a colon and indentation to separate code blocks.

## 1.7. Exceptions
```python
if size < 0:
    raise ValueError('number must be non-negative')
```
This `raise` statement is actually creating an instance of the `ValueError` class.
If one function doesn’t handle it, the exception is passed to the calling function, then that function’s calling function, and so on “up the stack.”
If the exception is never handled, your program will crash, Python will print a “traceback” to standard error.
### 1.7.1. Catching Import Errors
```python
try:
  import chardet
except ImportError:
  chardet = None
```
```python
try:
    from lxml import etree
except ImportError:
    import xml.etree.ElementTree as etree
```

## 1.8. Unbound Variables
You never declare the variable multiple, you just assign a value to it.
```python
multiple = 1024 if a_kilobyte_is_1024_bytes else 1000
```
## 1.9. Everything is Case-Sensitive
All names in Python are case-sensitive: variable names, function names, class names, module names, exception names.
## 1.10. Running Scripts
`import` the module
```python
>>> import humansize
>>> humansize.__name__
'humansize'
```

run the module directly as a standalone program, in which case `__name__` will be a special default value, `__main__`.

# 2. Native Datatypes
## 2.1. Diving In
1. **Booleans** are either `True` or `False`.
2. **Numbers** can be integers (`1` and `2`), floats (`1.1` and `1.2`), fractions (`1/2` and `2/3`), or even complex numbers.
3. **Strings** are sequences of Unicode characters, _e.g._ an html document.
4. **Bytes** and **byte arrays**, _e.g._ a jpeg image file.
5. **Lists** are ordered sequences of values.
6. **Tuples** are ordered, immutable sequences of values.
7. **Sets** are unordered bags of values.
8. **Dictionaries** are unordered bags of key-value pairs.
## 2.2. Booleans
```python
>>> size = 1
>>> size == 1
True
```
## 2.3. Numbers
```python
>>> type(2.0)
<class 'float'>
>>> type(1)
<class 'int'>
>>> type(2.0)
<class 'float'>
>>> isinstance(1, int)
True
>>> isinstance(1 + 2.0, int)
False
```
### 2.3.2. Common Numerical Operations
```python
>>> 11 / 2
5.5
>>> 11 // 2
5
>>> 11.0 / 2
5.5
>>> 11 ** 2
121
>>> 11 % 2
1
>>> -11 // 2
-6
>>> 11.0 // 2
5.0
```
### 2.3.3. Fractions
```python
>>> import fractions
>>> x = fractions.Fraction(1, 3)
>>> x
Fraction(1, 3)
>>> x * fractions.Fraction(1, 3)
Fraction(1, 9)
```
### 2.3.4. Trigonometry
```python
>>> import math
>>> math.tan(math.pi / 2)
1.633123935319537e+16
>>> math.tan(math.pi / 4)
0.9999999999999999
```
### 2.3.5. Numbers In A Boolean Context
Zero values are false, and non-zero values are true.
```python
>>> def is_it_true(anything):
...     if anything:
...         print("yes, it's true")
...     else:
...         print("no, it's false")
...
>>> is_it_true(1)
yes, it's true
>>> is_it_true(0)
no, it's false
```
## 2.4. Lists
### 2.4.1. Creating A List
```python
>>> a_list = ['a', 'b', 'mpilgrim', 'z', 'example']
>>> a_list
['a', 'b', 'mpilgrim', 'z', 'example']
>>> a_list[0]
'a'
>>> a_list[-1]
'example'
```
a_list[-n] == a_list[len(a_list) - n]
### 2.4.2. Slicing A List
```python
>>> a_list
['a', 'b', 'mpilgrim', 'z', 'example']
>>> a_list[1:3]
['b', 'mpilgrim']
>>> a_list[1:-1]
['b', 'mpilgrim', 'z']
>>> a_list[1:0]
[]
>>> a_list[1:-1]
['b', 'mpilgrim', 'z']
>>> a_list[1:4]
['b', 'mpilgrim', 'z']
>>> a_list[1:]
['b', 'mpilgrim', 'z', 'example']
```
### 2.4.3. Adding Items To A List
```python
>>> a_list = ['a']
>>> print(id(a_list))
4309370688
>>> a_list = a_list + [2.0, 3]
>>> print(id(a_list))
4309370432
>>> a_list
['a', 2.0, 3]
>>> a_list.append(True)
>>> a_list
['a', 2.0, 3, True]
>>> print(id(a_list))
4309370432
>>> a_list.extend(['four', 'Ω'])
>>> a_list
['a', 2.0, 3, True, 'four', 'Ω']
>>> print(id(a_list))
4309370432
>>> a_list.insert(0, 'Ω')
>>> a_list
['Ω', 'a', 2.0, 3, True, 'four', 'Ω']
>>> print(id(a_list))
4309370432
```
Let’s look closer at the difference between `append()` and `extend()`.
```python
>>> a_list = ['a', 'b', 'c']
>>> a_list.extend(['d', 'e', 'f'])
>>> a_list
['a', 'b', 'c', 'd', 'e', 'f']
>>> a_list[-1]
'f'
>>> a_list.append(['g', 'h', 'i'])
>>> a_list
['a', 'b', 'c', 'd', 'e', 'f', ['g', 'h', 'i']]
>>> a_list[-1]
['g', 'h', 'i']
>>> len(a_list)
7
```
### 2.4.4. Searching For Values In A List
```python
>>> a_list = ['a', 'b', 'new', 'mpilgrim', 'new']
>>> a_list.count('new')
2
>>> 'new' in a_list
True
>>> 'c' in a_list
False
>>> a_list.index('mpilgrim')
3
>>> a_list.index('c')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'c' is not in list
>>> a_list.index('new')
2
```
### 2.4.5. Removing Items From A List
```python
>>> a_list = ['a', 'b', 'new', 'mpilgrim', 'new']
>>> a_list[1]
'b'
>>> del a_list[1]
>>> a_list
['a', 'new', 'mpilgrim', 'new']
>>> a_list[1]
'new'
```

```python
>>> a_list.remove('new')
>>> a_list
['a', 'mpilgrim', 'new']
>>> a_list.remove('new')
>>> a_list
['a', 'mpilgrim']
>>> a_list.remove('new')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list
```
### 2.4.6. Removing Items From A List: Bonus Round
```python
>>> a_list = ['a', 'b', 'new', 'mpilgrim']
>>> a_list.pop()
'mpilgrim'
>>> a_list.pop(1)
'b'
>>> a_list
['a', 'new']
>>> a_list.pop()
'new'
>>> a_list.pop()
'a'
>>> a_list.pop()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: pop from empty list
```
### 2.4.7. Lists In A Boolean Context
Empty lists are false; all other lists are true.
```python
>>> def is_it_true(anything):
...    if anything:
...      print("yes, it's true")
...    else:
...      print("no, it's false")
...
>>> is_it_true([])
no, it's false
>>> is_it_true(['a'])
yes, it's true
>>> is_it_true([False])
yes, it's true
```
## 2.5. Tuples
A tuple is an immutable list.
```python
>>> a_tuple = ("a", "b", "mpilgrim", "z", "example")
>>> a_tuple[0]
'a'
>>> a_tuple[-1]
'example'
>>> a_tuple[1:3]
('b', 'mpilgrim')
>>> print(id(a_tuple))
4309516128
>>> print(id(a_tuple[1:3]))
4309521728
```
When you slice a list, you get a new list; when you slice a tuple, you get a new tuple.

```python
>>> a_tuple
('a', 'b', 'mpilgrim', 'z', 'example')
>>> a_tuple.append('new')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'append'
>>> a_tuple.remove('z')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'remove'
>>> a_tuple.index('example')
4
>>> "z" in a_tuple
True
```

So what are tuples good for?
1. Tuples are faster than lists.
2. “write-protect”
3. Some tuples can be used as dictionary keys.

```python
>>> list(('a', 'b'))
['a', 'b']
>>> tuple(['a', 'b'])
('a', 'b')
```

Tuples can be converted into lists, and vice-versa. In effect, `tuple()` freezes a list, and `list()` thaws a tuple.
### 2.5.1. Tuples In A Boolean Context
```python
>>> def is_it_true(anything):
...    if anything:
...      print("yes, it's true")
...    else:
...      print("no, it's false")
...
>>> is_it_true(())
no, it's false
>>> is_it_true((False,))
yes, it's true
>>> type((False,))
<class 'tuple'>
>>> type([False,])
<class 'list'>
```
### 2.5.2. Assigning Multiple Values At Once
```python
>>> v = ('a', 2, True)
>>> (x, y, z) = v
>>> x
'a'
>>> y
2
>>> z
True
```

```python
>>> (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY) = range(7)
>>> MONDAY
0
>>> SUNDAY
6
>>>
```
## 2.6. Sets
### 2.6.1. Creating A Set
```python
>>> a_set = {1}
>>> a_set
{1}
>>> type(a_set)
<class 'set'>
```

create a set out of a [list](https://diveintopython3.net/native-datatypes.html#lists).
```python
>>> a_list = ['a', 'b', 'mpilgrim', True, False, 42]
>>> a_set = set(a_list)
>>> a_set
{False, True, 'b', 42, 'a', 'mpilgrim'}
>>> a_list
['a', 'b', 'mpilgrim', True, False, 42]
```

create an empty set.
```python
>>> a_set = set()
>>> a_set
set()
>>> type(a_set)
<class 'set'>
>>> not_sure = {}
>>> type(not_sure)
<class 'dict'>
```
Due to historical quirks carried over from Python 2, you can not create an empty set with two curly brackets.

### 2.6.2. Modifying A Set
```python
>>> a_set = {1, 2}
>>> a_set.add(4)
>>> a_set
{1, 2, 4}
>>> a_set.update({2, 4, 6})
>>> a_set
{1, 2, 4, 6}
```
### 2.6.3. Removing Items From A Set
```python
>>> a_set = {1, 3, 6, 10, 15, 21, 28, 36, 45}
>>> a_set.discard(10)
>>> a_set
{1, 3, 36, 6, 45, 15, 21, 28}
>>> a_set.discard(10)
>>> a_set
{1, 3, 36, 6, 45, 15, 21, 28}
>>> a_set.remove(2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 2
>>> a_set.remove(1)
>>> a_set
{3, 36, 6, 45, 15, 21, 28}
```
If the value doesn’t exist in the set, the `remove()` method raises a `KeyError` exception.

```python
>>> a_set = {1, 3, 6, 10, 15, 21, 28, 36, 45}
>>> a_set.pop()
1
>>> a_set.pop()
3
>>> a_set.pop()
36
>>> a_set
{6, 10, 45, 15, 21, 28}
>>> a_set.clear()
>>> a_set.pop()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'pop from an empty set'
```
### 2.6.4. Common Set Operations
```python
>>> a_set = {2, 4, 5, 9, 12, 21, 30, 51, 76, 127, 195}
>>> 2 in a_set
True
>>> b_set = {1, 2, 3, 5, 6, 8, 9, 12, 15, 17, 18, 21}
>>> a_set.union(b_set)
{1, 2, 195, 4, 5, 3, 6, 8, 9, 12, 76, 15, 17, 18, 21, 30, 51, 127}
>>> a_set.intersection(b_set)
{2, 5, 9, 12, 21}
>>> a_set.difference(b_set)
{195, 4, 76, 51, 30, 127}
>>> a_set.symmetric_difference(b_set)
{1, 3, 195, 6, 4, 8, 76, 15, 17, 18, 51, 30, 127}
```
The `symmetric_difference()` method returns a new set containing all the elements that are in _exactly one_ of the sets.

Three of these methods are symmetric.
```python
>>> b_set.symmetric_difference(a_set)
{1, 195, 4, 3, 6, 8, 76, 15, 17, 18, 51, 30, 127}
>>> b_set.symmetric_difference(a_set) == a_set.symmetric_difference(b_set)
True
>>> b_set.union(a_set) == a_set.union(b_set)
True
>>> b_set.intersection(a_set) == a_set.intersection(b_set)
True
>>> b_set.difference(a_set) == a_set.difference(b_set)
False
```

```python
>>> a_set = {1, 2, 3}
>>> b_set = {1, 2, 3, 4}
>>> a_set.issubset(b_set)
True
>>> b_set.issuperset(a_set)
True
>>> a_set.add(5)
>>> a_set.issubset(b_set)
False
>>> b_set.issuperset(a_set)
False
```
### 2.6.5. Sets In A Boolean Context
```python
>>> def is_it_true(anything):
...    if anything:
...      print("yes, it's true")
...    else:
...      print("no, it's false")
...
>>> is_it_true(set())
no, it's false
>>> is_it_true({'a'})
yes, it's true
>>> is_it_true({False})
yes, it's true
```
## 2.7. Dictionaries
### 2.7.1. Creating A Dictionary
```python
>>> a_dict
{'server': 'db.diveintopython3.org', 'database': 'mysql'}
>>> a_dict['server']
'db.diveintopython3.org'
>>> a_dict['db.diveintopython3.org']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'db.diveintopython3.org'
```
### 2.7.2. Modifying A Dictionary
```python
>>> a_dict
{'server': 'db.diveintopython3.org', 'database': 'mysql'}
>>> a_dict['database'] = 'blog'
>>> a_dict
{'server': 'db.diveintopython3.org', 'database': 'blog'}
>>> a_dict['User'] = 'mark'
>>> a_dict
{'server': 'db.diveintopython3.org', 'database': 'blog', 'User': 'mark'}
```
### 2.7.3 Mixed-Value Dictionaries
Dictionary values can be any datatype, including integers, booleans, arbitrary objects, or even other dictionaries.
Dictionary keys are more restricted, but they can be strings, integers, and a few other types.
```python
>>> SUFFIXES = {1000: ['KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],
...              1024: ['KiB', 'MiB', 'GiB', 'TiB', 'PiB', 'EiB', 'ZiB', 'YiB']}
>>> len(SUFFIXES)
2
>>> 1000 in SUFFIXES
True
>>> SUFFIXES[1000]
['KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB']
>>> SUFFIXES[1000][3]
'TB'
```
### 2.7.4. Dictionaries In A Boolean Context
Empty dictionaries are false; all other dictionaries are true.
```python
>>> is_it_true({})
no, it's false
>>> is_it_true({'a': 1})
yes, it's true
```
## 2.8 `None`
`None` is the only null value. It has its own datatype (`NoneType`).
```python
>>> type(None)
<class 'NoneType'>
>>> None == False
False
>>> None == 0
False
>>> None == None
True
>>> None == ''
False
>>> x = None
>>> x == None
True
>>> y = None
>>> x == y
True
```
### 2.8.1. `None` In A Boolean Context
```python
>>> is_it_true(None)
no, it's false
>>> is_it_true(not None)
yes, it's true
```
# 3. Comprehensions
## 3.1 Diving In
Every programming language has that one feature, a complicated thing intentionally made simple. This chapter will teach you about list comprehensions, dictionary comprehensions, and set comprehensions.
## 3.2. Working With Files And Directories
### 3.2.1. The Current Working Directory
The current working directory is an invisible property that Python holds in memory at all times.
```python
>>> import os
>>> print(os.getcwd())
/Users/kagableed/Documents
>>> os.chdir('/Users/kagableed/Documents')
>>> print(os.getcwd())
/Users/kagableed/Documents
```
### 3.2.2. Working With Filenames and Directory Names
```python
>>> print(os.path.join('/Users/kagableed/Downloads/', 'humansize.py'))
/Users/kagableed/Downloads/humansize.py
>>> print(os.path.join('/Users/kagableed/Downloads', 'humansize.py'))
/Users/kagableed/Downloads/humansize.py
>>> print(os.path.expanduser('~'))
/Users/kagableed
>>> print(os.path.join(os.path.expanduser('~'), 'Download', 'humansize.py'))
/Users/kagableed/Download/humansize.py
```

```python
>>> pathname = '/Users/kagableed/Download/humansize.py'
>>> os.path.split(pathname)
('/Users/kagableed/Download', 'humansize.py')
>>> (dirname, filename) = os.path.split(pathname)
>>> dirname
'/Users/kagableed/Download'
>>> filename
'humansize.py'
>>> (shortname, extension) = os.path.splitext(filename)
>>> shortname
'humansize'
>>> extension
'.py'
```
### 3.2.3. Listing Directories
The `glob` module uses shell-like wildcards.
```python
>>> import glob
>>> glob.glob('*.log')
['java_error_in_goland_623.log', 'jbr_err_pid26969.log', 'jbr_err_pid14076.log', 'java_error_in_goland_14076.log', 'java_error_in_goland_38197.log', 'jbr_err_pid1051.log', 'java_error_in_phpstorm_26969.log', 'jbr_err_pid20754.log']
```
### 3.2.4. Getting File Metadata
```python
>>> import os
>>> print(os.getcwd())
/Users/kagableed
>>> metadata = os.stat('java_error_in_goland_623.log')
>>> metadata.st_mtime
1679028539.770996
>>> import time
>>> time.localtime(metadata.st_mtime)
time.struct_time(tm_year=2023, tm_mon=3, tm_mday=17, tm_hour=12, tm_min=48, tm_sec=59, tm_wday=4, tm_yday=76, tm_isdst=0)
```

```python
>>> metadata.st_size
384441
>>> os.chdir('/Users/kagableed/Downloads')
>>> import humansize
>>> humansize.approximate_size(metadata.st_size)
'375.4 KiB'
```
### 3.2.5. Constructing Absolute Pathnames
```python
>>> import os
>>> print(os.getcwd())
/Users/kagableed/Downloads
>>> print(os.path.realpath('humansize.py'))
/Users/kagableed/Downloads/humansize.py
```
## 3.3. List Comprehensions
You can use any Python expression in a list comprehension.
```python
>>> a_list = [1, 9, 8, 4]
>>> [elem ** 2 for elem in a_list]
[1, 81, 64, 16]
>>> a_list = [elem ** 2 for elem in a_list]
>>> a_list
[1, 81, 64, 16]
```

```python
>>> import os, glob
>>> glob.glob('*.py')
['humansize.py']
>>> [os.path.realpath(f) for f in glob.glob('*.py')]
['/Users/kagableed/Downloads/humansize.py']
```

```python
>>> import os, glob
>>> [(os.stat(f).st_size, os.path.realpath(f)) for f in glob.glob('*.log') if os.stat(f).st_size > 10000 ]
[(384441, '/Users/kagableed/java_error_in_goland_623.log'), (292827, '/Users/kagableed/java_error_in_goland_14076.log'), (262612, '/Users/kagableed/java_error_in_goland_38197.log'), (280394, '/Users/kagableed/java_error_in_phpstorm_26969.log')]
```
## 3.4. Dictionary Comprehensions
```python
>>> import os, glob
>>> metadata = [(f, os.stat(f)) for f in glob.glob('*.log')]
>>> type(metadata)
<class 'list'>
>>> type(metadata[0])
<class 'tuple'>
>>> metadata[0]
('java_error_in_goland_623.log', os.stat_result(st_mode=33188, st_ino=34961543, st_dev=16777232, st_nlink=1, st_uid=501, st_gid=20, st_size=384441, st_atime=1679028542, st_mtime=1679028539, st_ctime=1679028539))
>>> metadata_dict = {f:os.stat(f) for f in glob.glob('*.log')}
>>> type(metadata_dict)
<class 'dict'>
>>> list(metadata_dict.keys())
['java_error_in_goland_623.log', 'jbr_err_pid26969.log', 'jbr_err_pid14076.log', 'java_error_in_goland_14076.log', 'java_error_in_goland_38197.log', 'jbr_err_pid1051.log', 'java_error_in_phpstorm_26969.log', 'jbr_err_pid20754.log']
>>> metadata_dict['java_error_in_goland_623.log'].st_size
384441
```
### 3.4.1. Other Fun Stuff To Do With Dictionary Comprehensions
swapping the keys and values of a dictionary.
```python
>>> a_dict = {'a': 1, 'b': 2, 'c': 3}
>>> {value:key for key, value in a_dict.items()}
{1: 'a', 2: 'b', 3: 'c'}
```

```python
>>> a_dict = {'a': [1, 2, 3], 'b': 4, 'c': 5}
>>> {value:key for key, value in a_dict.items()}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 1, in <dictcomp>
TypeError: unhashable type: 'list'
```

```python
>>> a_dict = {'a': (1, 2, 3), 'b': 4, 'c': 5}
>>> {value:key for key, value in a_dict.items()}
{(1, 2, 3): 'a', 4: 'b', 5: 'c'}
```

```python
>>> a_dict = {'a': {1: 2}, 'b': 4, 'c': 5}
>>> {value:key for key, value in a_dict.items()}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 1, in <dictcomp>
TypeError: unhashable type: 'dict'
```
## 3.5. Set Comprehensions
```python
>>> a_set = set(range(10))
>>> a_set
{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
>>> {x ** 2 for x in a_set}
{0, 1, 64, 4, 36, 9, 16, 49, 81, 25}
>>> {x ** 2 for x in a_set if x % 2 == 0}
{0, 64, 4, 36, 16}
```
# 4. Strings
## 4.1. Some Boring Stuff You Need To Understand Before You Can Dive In
Everything you thought you knew about strings is wrong, and there ain’t no such thing as “plain text.”
## 4.2. Unicode
Unicode is a system designed to represent _every_ character from _every_ language. There is exactly 1 number per character, and exactly 1 character per number.

# todo


