# Code Guidelines
###### School Simplified IT Dept. - Bot Development

<br>
<br>

###### Written and proved by Puncher - If you have any questions don't hesitate to ask me.

###### *These guidelines are subject to change at any time.*

## 0. Table of Contents
  - [0. Table of Contents](#0-table-of-contents)
  - [1. Introduction](#1-introduction)
  - [2. Usage](#2-usage)
  - [3. Code Layout](#3-code-layout)
    - [3.1. Indentation](#31-indentation)
      - [3.1.1. Function definition and call](#311-function-definition-and-call)
      - [3.1.2. If-Statements](#312-if-statements)
      - [3.1.3. Closing brace/bracket/parenthesis](#313-closing-bracebracketparenthesis)
    - [3.2. Line Length](#32-line-length)
    - [3.3. Line Break at Operators](#33-line-break-at-operators)
    - [3.4. Blank Lines](#34-blank-lines)
    - [3.5. Imports](#35-imports)
    - [3.6. Module Level Dunder Names](#36-module-level-dunder-names)
  - [4. String Quotes](#4-string-quotes)
  - [5. Whitespace in Expressions and Statements](#5-whitespace-in-expressions-and-statements)
    - [5.1. Pet Peeves](#51-pet-peeves)
    - [5.2. Other important things](#52-other-important-things)
  - [6. Comments](#6-comments)
    - [6.1. Documentation Strings](#61-documentation-strings)
  - [7. Naming Conventions](#7-naming-conventions)
    - [7.1. Descriptive: Naming Styles](#71-descriptive-naming-styles)
    - [7.2. Prescriptive: Naming Conventions](#72-prescriptive-naming-conventions)
      - [7.2.1. Package and Module Names](#721-package-and-module-names)
      - [7.2.2. Class Names](#722-class-names)
      - [7.2.3. Function and Variable Names](#723-function-and-variable-names)
      - [7.2.4. Method Names and Instance Variables](#724-method-names-and-instance-variables)
      - [7.2.5. Constants](#725-constants)
  - [8. Programming](#8-programming)
    - [8.1. General](#81-general)
      - [8.1.1. Comparisons](#811-comparisons)
      - [8.1.2. Exceptions](#812-exceptions)
      - [8.1.3. Return Statements](#813-return-statements)
      - [8.1.3. Loops](#813-loops)
      - [8.1.4. Others](#814-others)
    - [8.2. Discord.py](#82-discordpy)
    - [8.3. Environment](#83-environment)

<br>
<br>

## 1. Introduction
To understand code better and faster and to have consistency through the code, it’s important to follow and adhere to code guidelines. Code guidelines is about consistency, which is very important.<br>
This document provides the guidelines for Python Code at School Simplified IT Dept. – Bot Development and is intended to be a reference of compliance with those guidelines. The guidelines are based on the [PEP8 – Style Guide for Python Code](https://peps.python.org/pep-0008/) and also provides internal guidelines to work with the library [discord.py](https://github.com/Rapptz/discord.py) and the environment of the bot.



<br>
<br>

## 2. Usage

These guidelines must be applied on the `main` branch. However it's an advantage if this is already taken care of in the `beta` branch. Pull requests to the `main` branch containing code that violates the code guidelines will be rejected.

<br>
<br>

## 3. Code Layout

### 3.1. Indentation
Use 4 spaces for one indentation level. **In PyCharm, 1 tab is already 4 spaces by default.**

#### 3.1.1. Function definition and call
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

#### 3.1.2. If-Statements
For `if`-statements there are no specific rules on how to indent. However, acceptable options include, but are not limited to:

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

#### 3.1.3. Closing brace/bracket/parenthesis
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

### 3.2. Line Length

**<ins>We don't apply this rule<ins/>**, even when PEP8 requires to limit all lines to a maximum length of 79 characters. However, limit it to something reasonable.

The preffered way to wrapping long lines is by using the Python's implied line continuation inside brackets. Long lines can also be broken over multiple lines by using a **backslash** for line continuation if it's needed.

```py

# Python's implied line continuation inside brackets
if (1 == 1 and 2 == 2
    or 3 == 3 and 4 == 4)

# Backslash line continuation
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())

```

<br>

### 3.3. Line Break at Operators

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

### 3.4. Blank Lines

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

### 3.5. Imports

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

### 3.6. Module Level Dunder Names
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

## 4. String Quotes
In Python, single-quoted strings and double-quoted strings are the same. You can either use double-quotes (`"Hello World!"`) or single quotes (`'Hello World!'`).

**For triple-quoted strings, always use <ins>double quotes</ins> to be consistent with the docstring convention.** 

<br>
<br>

## 5. Whitespace in Expressions and Statements

### 5.1. Pet Peeves
Avoid extraneous whitespace in the following situations:
* Immediately inside parentheses, brackets or braces:
  
  ```py
  # Correct:
  spam(ham[1], {eggs: 2})
  ```
  ```py
  # Wrong:
  spam( ham[ 1 ], { eggs: 2 } )
  ```
* Between a trailing comma and a following close parenthesis:
  
  ```py
  # Correct:
  foo = (0,)
  ```
  ```py
  # Wrong:
  bar = (0, )
  ```
* Immediately before a comma, semicolon, or colon:
  ```py
  # Correct:
  if x == 4: print(x, y); x, y = y, x
  ```
  ```py
  # Wrong:
  if x == 4 : print(x , y) ; x , y = y , x
  ```
* However, in a slice the colon acts like a binary operator, and should have equal amounts on either side (treating it as the operator with the lowest priority). In an extended slice, both colons must have the same amount of spacing applied. Exception: when a slice parameter is omitted, the space is omitted:

  ```py
  # Correct:
  ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
  ham[lower:upper], ham[lower:upper:], ham[lower::step]
  ham[lower+offset : upper+offset]
  ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
  ham[lower + offset : upper + offset]
  ```
  ```py
  # Wrong:
  ham[lower + offset:upper + offset]
  ham[1: 9], ham[1 :9], ham[1:9 :3]
  ham[lower : : upper]
  ham[ : upper]
  ```
* Immediately before the open parenthesis that starts the argument list of a function call:
  ```py
  # Correct:
  spam(1)
  ```
  ```py
  # Wrong:
  spam (1)
  ```
* Immediately before the open parenthesis that starts an indexing or slicing:
  ```py
  # Correct:
  dct['key'] = lst[index]
  ```
  ```py
  # Wrong:
  dct ['key'] = lst [index]
  ```
* More than one space around an assignment (or other) operator to align it with another:

  ```py
  # Correct:
  x = 1
  y = 2
  long_variable = 3
  ```
  ```py
  # Wrong:
  x             = 1
  y             = 2
  long_variable = 3
  ```

<br>

### 5.2. Other important things 

* Avoid trailing whitespace anywhere. Because it’s usually invisible, it can be confusing: e.g. a backslash followed by a space and a newline does not count as a line continuation marker.
* Always surround these binary operators with a single space on either side: assignment (`=`), augmented assignment (`+=`, `-=` etc.), comparisons (`==`, `<`, `>`, `!=`, `<>`, `<=`, `>=`, `in`, `not in`, `is`, `is not`), Booleans (`and`, `or`, `not`).
* If operators with different priorities are used, consider adding one whitespace around the operators with the lowest priority(ies).

  ```py
  # Correct:
  i = i + 1
  submitted += 1
  x = x*2 - 1
  hypot2 = x*x + y*y
  c = (a+b) * (a-b)
  ```
  ```py
  # Wrong:
  i=i+1
  submitted +=1
  x = x * 2 - 1
  hypot2 = x * x + y * y
  c = (a + b) * (a - b)
  ```
* Function annotations should use the normal rules for colons and always have spaces around the `->` if present:

  ```py
  # Correct:
  def munge(input: AnyStr): ...
  def munge() -> PosInt: ...
  ```
  ```py
  # Wrong:
  def munge(input:AnyStr): ...
  def munge()->PosInt: ...
  ```
* Don’t use spaces around the `=` sign when used to indicate a keyword argument, or when used to indicate a default value for an *unannotated* function parameter:

  ```py
  # Correct:
  def complex(real, imag=0.0):
      return magic(r=real, i=imag)
  ```
  ```py
  # Wrong:
  def complex(real, imag = 0.0):
      return magic(r = real, i = imag)
  ```
  When combining an argument annotation with a default value, however, do use spaces around the `=` sign:
  ```py
  # Correct:
  def munge(sep: AnyStr = None): ...
  def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...
  ```
  ```py
  # Wrong:
  def munge(input: AnyStr=None): ...
  def munge(input: AnyStr, limit = 1000): ...
  ```
* Don't use multiple statements on the same line
  ```py
  # Wrong
  if foo == 'blah': do_blah_thing()
  do_one(); do_two(); do_three()
  ```
  Rather do:
  ```py
  # Correct:
  if foo == 'blah':
      do_blah_thing()
  do_one()
  do_two()
  do_three()
  ```
  Definitely not:
  ```py
  # Wrong:
  if foo == 'blah': do_blah_thing()
  else: do_non_blah_thing()

  try: something()
  finally: cleanup()

  do_one(); do_two(); do_three(long, argument,
                               list, like, this)

  if foo == 'blah': one(); two(); three()
  ```

<br>
<br>

## 6. Comments
Comments that contradict the code are worse than no comments. Always make a priority of keeping the comments up-to-date when the code changes! Ensure that your comments are clear and easily understandable to others.

<br>

### 6.1. Documentation Strings
* Write docstrings for **all public modules, functions, classes and methods.** For non-public (`def __foo(): ...`) methods you don't have to use docstrings. A description with a comment is useful though. This comment should appear after the `def` line.

Multiline docstrings:
```py
"""
Return a foobang

Optional plotz says to frobnicate the bizbaz first.
"""
```
One liner docstrings:
```py
"""Return an ex-parrot."""
```

<br>
<br>

## 7. Naming Conventions

### 7.1. Descriptive: Naming Styles
The following naming styles are commonly used:
* `b` (single lowercase letter)
* `B` (single uppercase letter)
* `lowercase`
* `lower_case_with_underscores`
* `UPPERCASE`
* `UPPER_CASE_WITH_UNDERSCORES`
* `CamelCase` 
  <br>Note: When using acronyms in CamelCase, capitalize all the letters of the acronym. HTTPServerError is better than HttpServerError.
* `mixedCase`
* `Capitalized_Words_With_Underscores` (<ins>**Dont use this**</ins>)

In addition, the following special forms using leading or trailing underscores are recognized (these can generally be combined with any case convention):
* `_single_leading_underscore`: weak “internal use” indicator. E.g. `from <module> import *` does not import objects whose names start with one underscore.
* `single_trailing_underscore_`: used by convention to avoid conflicts with Python keyword, e.g.
  ```py
  tkinter.Toplevel(master, class_='ClassName')
  ```
* `__double_leading_underscore`: when naming a class attribute in class `FooBar`, `__boo` becomes `_FooBar__boo`. Means invoking`FooBar.__boo` won't work.
* `__double_leading_and_trailing_underscore__`: “magic” objects or attributes that live in user-controlled namespaces. E.g. `__init__`, `__import__` or `__file__`. **Never invent such names; only use them as documented.**

<br>

### 7.2. Prescriptive: Naming Conventions
**Names to avoid as single character variable names**:
* `l` (loweercase letter "el")
* `O` (uppercase letter "oh")
* `I` (uppercase letter "eye")
  In some fonts these characters are indistinguishable.


#### 7.2.1. Package and Module Names
Short, all-lowercase names. Underscores only if it improves readability (e.g. `utils.py`, `file_reader.py`)

#### 7.2.2. Class Names
CamelCase convention (e.g. `class FooBar`)

#### 7.2.3. Function and Variable Names
Lowercase, with words separated by underscores for readability.
```py
# Correct:
def create_foo():
  my_var = "string"
  num = 1
```

#### 7.2.4. Method Names and Instance Variables
Same name conventions as for [Function and Variable Names](#673-function-and-variable-names).

**Avoid variable name clashes:**
* Use one leading underscore for **protected variables which should be accessible for subclasses but not for the outside**.  -> `_my_var`, `_create_foo`
* Use two leading underscores for **"private" attributes which should only be accessible for the base class but not for the subclasses and the outside**. -> `__my_var`, `__create_foo`
* Use one trailing underscore **only to avoid collissions with a reserved keyword**. -> `tkinter.Toplevel(master, class_='ClassName')`

**Note:** In Python no attribute is really private. If class `FooBar` has an attribute named `__bar`, it cannot be accessed by `FooBar.__bar` but by `FooBar._FooBar__bar`.

#### 7.2.5. Constants
Defined on a module level and written in all capital letters with underscores for separating words. (e.g. `MAX_TIME`, `TOTAL`)

<br>
<br>

## 8. Programming

### 8.1. General

See [Discord.py](#72-discordpy) for discord.py-specific rules. The following rules are general rules.

#### 8.1.1. Comparisons

* For `True`, `False` and `None` use `is` resp. `is not` instead of the equality operators. 
* Use `is not` instead of `not ... is `. Both are technically the same but it's more readable:
  ```py
  # Correct:
  if foo is not None:
  ```
  ```py
  # Wrong:
  if not foo is None:
  ```

* Use `''.startswith()` and `''.endswith()` instead of string slicing to    check for prefixes or suffixes. `startswith()` and `endswith()` are cleaner and less error prone:
  ```py
  # Correct:
  if foo.startswith('bar'):
  ```
  ```py
  # Wrong:
  if foo[:3] == 'bar':
  ```

* Object type comparisons should always use isinstance() instead of comparing types directly:
  ```py
  # Correct:
  if isinstance(obj, int):
  ```
  ```py
  # Wrong:
  if type(obj) is type(1):
  ```

* For sequences, (strings, lists, tuples), use the fact that empty sequences are false:
  ```py
  # Correct:
  if not seq:
  if seq:
  ```
  ```py
  # Wrong:
  if len(seq):
  if not len(seq):
  ```

#### 8.1.2. Exceptions

* Derive/Inherit exceptions from `Exception` rather than `BaseException`.
* When catching excpetions don't use bare `except`. Mention specific exceptions whenever possible:
  ```py
  try:
    import platform_specific_module
  except ImportError:
    platform_specific_module = None
  ```
  `except` is equivalent to `except BaseException` which will also catch `SystemExit` and `KeyboardInterrupt` exceptions. Use `except Exception` instead if you want to catch all program errors.

* Additionally, for all try/except clauses, limit the try clause to the absolute minimum amount of code necessary. Again, this avoids masking bugs:
  ```py
  # Correct:
  try:
      value = collection[key]
  except KeyError:
      return key_not_found(key)
  else:
      return handle_value(value)
  ```
  ```py
  # Wrong:
  try:
      # Too broad!
      return handle_value(collection[key])
  except KeyError:
      # Will also catch KeyError raised by handle_value()
      return key_not_found(key)
  ```

#### 8.1.3. Return Statements

`return None`, `return` and no `return` at all will return `None` in the end. 
However, each should be used differently.<br>

* Use `return None` if the function is actually meant to return a value in another case:

  ```py
  def foo(x):
      if x >= 0:
          return math.sqrt(x)
      else:
          return None

  def bar(x):
      if x < 0:
          return None
      return math.sqrt(x)
  ```
* Use `return` if the function doesn't return anything at all. It's used for the same reason as `break` in loops or if you want to leave the function and the return value is not meant to be used or caught:

  ```py
  def foo(guests):
      for guest in guests:
          if human.knife:
              call_police()
              return

      enter_party()
  ```
  ```py
  def set_foo(arg):
      if isinstance(arg, int):
          return
      
      self.var = arg
  ```
* Use `return` **not at all** if the return value is not meant to be used or caught:
  ```py
  def set_knife(guest, knife):
      if is_human(guest):
          guest.knife = knife
  ```

#### 8.1.3. Loops

* If you need the index in a `for` loop, use `enumerate` instead of using an increment variable. It's less error prone and easier to read:
  ```py
  # Correct:
  for i, guest in enumerate(guests):
    # ...
  ```
  ```py
  # Wrong:
  i = 0
  for guest in guests:
    # ...
    i += 1
  ```

* If you want to iterate over two iteratables, use `zip`:
  ```py
  a = [1, 2, 3]
  b = [4, 5, 6]

  for av, bv in zip(a, b):
    # ...
  ```
  
  And if you need the index, use  `enumerate` and `zip` in combination:
  ```py
  a = [1, 2, 3]
  b = [4, 5, 6]

  for i, (av, bv) in enumerate(zip(a, b)):
    # ...

* If you iterate over a dict, use `dict.items()` to get the key and value:
  ```py
  # Correct:
  d = {"a": 1, "b": 2, "c": 3}
  for key, value in d.items():
    # ...
  ```
  ```py
  # Wrong:
  d = {"a": 1, "b": 2, "c": 3}
  for key in d:
    value = d[key]
  ```

#### 8.1.4. Others

* To get all elements of a tuple use unpacking not indexing:

  ```py
  # Correct:
  my_tuple = (1, 2)
  x, y = my_tuple
  ```
  ```py
  # Wrong:
  my_tuple = (1, 2)
  x = my_tuple[0]
  y = my_tuple[1]
  ```
* Use comprehensions on dicts, lists, sets and generators. However use it sensibly. Sometimes it's easier to read when just using `for` loops:
  ```py
  # Good Readability:
  dict_comp = {i: i * i for i in range(10)}
  list_comp = [x*x for x in range(10)]
  set_comp = {i%3  for i in range(10)}
  gen_comp = (2*x+5 for x in range(10))
  ```
  ```py
  # Bad Readability:
  comp = [
    sum(a[n * i + k] * b[n * k + j] for k in range(n))
    for i in range(n)
    for j in range(n)
    ]
  ```
* When using `\n` in strings, really make a new line in the code for better readability:
  ```py
  # Correct: 
  my_string = "Hello this is an example text." \
              "\nThanks for reading."
  ```
  ```py
  # Wrong:
  my_string = "Hello this is an example text.\nThanks for reading."
  ```
  **Tip:** In most IDEs, when you hit the enter key inside a string it will automatically continue the string on the new line.

<br>

### 8.2. Discord.py

* Whenever it's possible, use `get_x` instead of `fetch_x`. `fetch_x` causes unnecessary API calls, which should be limited to a minimum. Get it from the cache instead.

* When using the decorators for `app_commands` or `commands` use also the module's name in the decorator to avoid name clashing and provide a better readability:
  ```py
  # Correct:
  @commands.command()
  async def my_command(self, ctx: commands.Context):
    # ...
  
  @app_commands.command(name="my_slash_command")
  async def my_slash_command(self, interaction: discord.Interaction)
    # ...
  ```
  ```py
  # Wrong:
  from app_commands import command
  
  @command(name="my_slash_command")
  async def my_slash_command(self, interaction: discord.Interaction)
    # ...
  ```

* For event and command functions, use typehints for all parameters:
  ```py
  @commands.command()
  async def my_command(self, ctx: commands.Context, member: discord.Member):
    # ...
  ```

* Don't use raw IDs e.g. `932066545117585428`. Create variables in `core/common.py` in the specific class instead and add it to ConfigCat.

<br>

### 8.3. Environment

* For constant objects, constant variables and Discord IDs use the modules in `core`:
  
  ```py
  # Correct:
  from core.common import Colors

  embed = discord.Embed(color=Colors.red)
  ```
  ```py
  # Wrong:
  embed = discord.Embed(color=0xff0000)
  ```
