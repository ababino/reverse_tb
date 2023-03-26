reverse_tb
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Install

``` sh
pip install reverse_tb
```

## How to use

``` python
from reverse_tb.core import reverse_tb
```

``` python
def foo():
    return bar()

def bar():
    return baz()

def baz():
    try:
        qux()
    except KeyError as e:
        raise Exception
    return qux()

def qux():
    d = {}
    return d['key']
```

``` python
foo()
```

    Exception: 

``` python
foo()
```

    ---------------------------------------------------------------------------
    Exception: 
    Cell In[3], line 11, in baz()
          9     qux()
         10 except KeyError as e:
    ---> 11     raise Exception
         12 return qux()

    Cell In[3], line 5, in bar()
          4 def bar():
    ----> 5     return baz()

    Cell In[3], line 2, in foo()
          1 def foo():
    ----> 2     return bar()

    Cell In[5], line 1
    ----> 1 foo()

    Exception                                 Traceback (last call first)

    During handling of the above exception, another exception occurred:

    KeyError: 'key'
    Cell In[3], line 16, in qux()
         15 d = {}
    ---> 16 return d['key']
            d = {}

    Cell In[3], line 9, in baz()
          8 try:
    ----> 9     qux()
         10 except KeyError as e:

    KeyError                                  Traceback (last call first)
