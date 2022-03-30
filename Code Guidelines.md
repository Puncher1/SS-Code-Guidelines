# Code Guidelines
###### School Simplified IT Dept. - Bot Development

<br>
<br>
<br>

## 0. Table of Contents
  - [0. Table of Contents](#0-table-of-contents)
  - [1. Introduction](#1-introduction)
  - [2. Code Layout](#2-code-layout)
    - [2.1. Indentation](#21-indentation)
      - [2.1.1. Function definition and call](#211-function-definition-and-call)
      - [2.1.2. If-Statements](#212-if-statements)
      - [2.1.3. Closing brace/bracket/parenthesis](#213-closing-bracebracketparenthesis)
    - [2.2. Line Length](#22-line-length)
    - [2.3. Line Break at Operators](#23-line-break-at-operators)
    - [2.4. Blank Lines](#24-blank-lines)
    - [2.5. Imports](#25-imports)
    - [2.6. Module Level Dunder Names](#26-module-level-dunder-names)
  - [3. String Quotes](#3-string-quotes)
  - [4. Whitespace in Expressions and Statements](#4-whitespace-in-expressions-and-statements)

<br>
<br>

## 1. Introduction
To understand code better and faster and to have consistency through the code, it’s important to follow and adhere to code guidelines. Code guidelines is about consistency. Consistency in code is important. Consistency within a project is more important. Consistency within one module or function is the most important. 
This document provides the guidelines for Python Code at School Simplified IT Dept. – Bot Development and is intended to be a reference of compliance with those guidelines. The guidelines are based on the [PEP8 – Style Guide for Python Code](https://peps.python.org/pep-0008/) and the [PEP257 – Docstring Conventions](https://peps.python.org/pep-0257/) and also provides internal guidelines to work with the library [discord.py](https://github.com/Rapptz/discord.py).

<br>
<br>

## 2. Code Layout

### 2.1. Indentation
Use 4 spaces for one indentation level. **In PyCharm, 1 tab is 4 spaces.**

#### 2.1.1. Function definition and call
```py
# Correct:

# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

```
```py
# Wrong:

# Arguments on first line forbidden when not using vertical alignment.
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# Further indentation required as indentation is not distinguishable.
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

#### 2.1.2. If-Statements
For `if`-statements there are no specific rules on how to do indent. However, acceptable options include, but are not limited to:
```py
# No extra indentation.
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# No extra indentation with an empty line after if-statement.
# PREFERRED
if (this_is_one_thing and
    that_is_another_thing):
    
    do_something()
```

#### 2.1.3. Closing brace/bracket/parenthesis
The closing brace/bracket/parenthesis on multiline constructs may either line up under the first non-whitespace character of the last line of list, as in:
```py
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```
or it may be lined up under the first character of the line that starts the multiline construct, as in:
```py
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

<br>

### 2.2. Line Length

**<ins>We don't apply this rule<ins/>**, even when PEP8 requires to limit all lines to a maximum length of 79 characters. However, limit it to something reasonable. In PyCharm the limit is 120 characters by default which is marked with a thin, grey line.

<span style="color:red">**IMAGE HERE**</span>

The preffered way to wrapping long lines is by using the Python's implied line continuation inside brackets. Long lines can also be broken over multiple lines by using a **backslash** for line continuation if it's needed.

```py

# Python's implied line continuation inside brackets
if (True == True and False == False
    or False == False and True == True)

# Backslash line continuation
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())

```

<br>

### 2.3. Line Break at Operators

For readability it's recommended to line break **before** the operator (see below). However, it's <ins>not mandatory.</ins>
```py
# Recommended:

income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

<br>

### 2.4. Blank Lines

**Top-level classes and functions:** Surrounded by 2 blank lines
```py
import sys


class Foo:
    # ...


def func():
    # ...
```
**Methods inside a class:** Surrounded by 1 blank line
```py
class Foo:

    def foo():
        # ...

    def boo():
        # ...
```
Extra blank lines may be used (sparingly) to separate groups of code. However it should be reasonable, means no extra blank lines between a bunch of one-liners.
```py
# Correct:

from datetime import datetime, timedelta

# Block 1: Calculation
factor_1 = 1 + 1
factor_2 = 2 + 2
result = factor_1 * factor_2

# Block 2: Datetime creation
now = datetime.now()
time_add = timedelta(hours=result)
dt = now + time_add
```
```py
# Wrong:

from datetime import datetime, timedelta

result = (1+1) * (2+2)
# this blank line is unnecessary
now = datetime.now() + timedelta(hours=result)
```

<br>

### 2.5. Imports

* Imports should be on separate lines.
    ```py
    # Correct:
    import sys
    import os
    ```
    ```py
    # Wrong:
    import sys, os
    ```
    Imports like `from ... import` on one line is **allowed**.
    ```py
    from discord.ext import commands, menus
    ```
* Imports are always at the top of the file, just after any module comments and docstrings, and before module variables and constants

    Also, imports should  be **grouped** in the following order: <br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Standard library imports<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Related third party imports<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Local application/library specific imports

    Between each group put a **blank line** and sort it **alphabetically**.
    ```py
    """
    This module puts a random number into a google spreadsheet cell.
    """

    # Standard library imports
    import random

    # Related third party imports
    import gspread  

    # Local application/library specific imports
    from core.common import GOOGLE_CREDS


    # Module variables
    gspread_user = GOOGLE_CREDS["username"]
    gspread_pw = GOOGLE_CREDS["password"]
    ```
    To sort the imports, you can use [isort](https://pypi.org/project/isort/) which does that for you.

* Wildcard imports (`from <module> import *`) should be avoided, as they make it unclear which names are present in the namespace, confusing both readers and many automated tools. It's also prone for bugs. 

<br>

### 2.6. Module Level Dunder Names
Module level “dunders” (i.e. names with two leading and two trailing underscores) such as `__all__`, `__author__`, `__version__`, etc. should be placed after the module docstring but before any import statements except `from __future__` imports. Python mandates that future-imports must appear in the module before any other code except docstrings:
```py
"""
This module handles stuff.
"""

from __future__ import barry_as_FLUFL

__all__ = ['a', 'b', 'c']
__version__ = '0.1'
__author__ = 'School Simplified IT Dept. - Bot Development'

import os
import sys
```

<br>
<br>

## 3. String Quotes
In Python, single-quoted strings and double-quoted strings are the same. You can either use double-quotes (`"Hello World!"`) or single quotes (`'Hello World!'`).

**For triple-quoted strings, always use <ins>double quotes</ins> to be consistent with the docstring convention.** 

<br>
<br>

## 4. Whitespace in Expressions and Statements