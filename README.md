# slyle-guidelines


## Setting a Custom Git Commit Message Template
By setting a custom Git commit message template, you can ensure that your commit messages follow a consistent format and contain all the necessary information for your team or collaborators to understand the changes being made in the repository.

To set a custom Git commit message template for your repository, follow these steps:

1. Download the *git_commit_template.txt* file.

2. Open your terminal or command prompt and navigate to your Git repository.

3. Set the *commit.template* configuration option to the path of your custom template file by using the following command:

<pre>
&emsp;git config --global commit.template git_commit_template.txt
</pre>

Note that the *--global* option sets the configuration globally for all Git repositories on your machine. If you only want to set the configuration for the current repository, you can omit the *--global* option.

The next time you create a commit, Git will use your custom template as the default commit message. You can still modify the message as needed before finalizing the commit.

## Google Python Style Guide

This guide describes the recommended coding style for Python programs at Google. It is based on the PEP 8 style guide, but adds some additional guidelines for consistency with other Google programming languages.

### Table of Contents

- [Line Length](#line-length)
- [Indentation](#indentation)
- [Naming Conventions](#naming-conventions)
- [String Quotes](#string-quotes)
- [Whitespace](#whitespace)
- [Comments and Docstrings](#comments-and-docstrings)
- [Programming Recommendations](#programming-recommendations)
- [Imports](#imports)
- [Testing](#testing)


### Semicolons

- Do not use semicolons to put two statements on the same line.

### [Line Length](https://google.github.io/styleguide/pyguide.html#32-line-length)

- Limit lines to a maximum of 80 characters.
- Break long lines using parentheses or string concatenation.
- Within comments, put long URLs on their own line if necessary.

```python
# Break long lines using parentheses
result = (value1 + value2 + value3
          + value4 + value5)
          
long_string = ('This is a very long string that needs to be broken up '
               'into multiple lines for readability. It can be done using '
               'parentheses, backslashes, or string concatenation.')

# Break long lines using string concatenation
result = value1 + value2 + value3 + \
         value4 + value5
         
long_string = 'This is a very long string that needs to be broken up ' + \
              'into multiple lines for readability. It can be done using ' + \
              'string concatenation.'
              
# URLs within comments
# See details at
# http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```

### [Indentation](https://google.github.io/styleguide/pyguide.html#34-indentation)

- Use 4 spaces for indentation.
- Never use tabs or mix tabs and spaces.
- Align the closing parentheses with the start of the line that contains the corresponding opening parentheses.
- *how to configure this in VScode*
          
```python
# 1. Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
meal = (spam,
        beans)

# 1. Aligned with opening delimiter in a dictionary.
foo = {
   'long_dictionary_key': value1 +
                          value2,
   ...
}

# 2. 4-space hanging indent; nothing on first line.
foo = long_function_name(
   var_one, var_two, var_three,
   var_four)
meal = (
   spam,
   beans)

# 3. 4-space hanging indent; nothing on first line,
# closing parenthesis on a new line.
foo = long_function_name(
   var_one, var_two, var_three,
   var_four
)
meal = (
   spam,
   beans,
)

# 3. 4-space hanging indent in a dictionary.
foo = {
    'long_dictionary_key':
        long_dictionary_value,
   ...
}  
```  

### [Comments and Docstrings](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings)

Python uses docstrings to document code. A docstring is a string that is the first statement in a package, module, class or function. 

- Docstrings are the first statement in packages, modules, classes, or functions.
- Use triple-double-quote """ format (PEP 257).
- Organize as a summary line (≤80 characters) terminated by a period, question mark, or exclamation point
- Optional: blank line followed by additional details with consistent indentation.


#### [Punctuation, Spelling and Grammar](https://google.github.io/styleguide/pyguide.html#386-punctuation-spelling-and-grammar)

Pay attention to punctuation, spelling, and grammar; it is easier to read well-written comments than badly written ones.

Comments should be as readable as narrative text, with proper capitalization and punctuation. In many cases, complete sentences are more readable than sentence fragments. Shorter comments, such as comments at the end of a line of code, can sometimes be less formal, but you should be consistent with your style.


#### [Modules](https://google.github.io/styleguide/pyguide.html#382-modules)

- Every file should contain license boilerplate.
- Files should start with a docstring describing the contents and usage of the module.


```python
"""A one-line summary of the module or program, terminated by a period.

Leave one blank line.  The rest of this docstring should contain an
overall description of the module or program.  Optionally, it may also
contain a brief description of exported classes and functions and/or usage
examples.

Typical usage example:

  foo = ClassFoo()
  bar = foo.FunctionBar()
  
This module provides:

- Feature 1
- Feature 2
- ...

Author: Your Name
Email: your_email@example.com
Date: Date created
"""
```
         

#### [Functions and methods](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods)

- Functions and methods require a docstring if:
  - Part of the public API.
  - Nontrivial size.
  - Non-obvious logic.
- Docstrings should provide enough information to call the function without reading its code.
- Use consistent style within a file: descriptive or imperative.
- Overriding methods can reference base class docstrings, unless behavior is substantially different.
- Special sections for documentation:
  - Args: List parameters by name, description, and type (if not in type annotation).
  - Returns (or Yields for generators): Describe type and semantics of the return value.
  - Raises: List relevant exceptions and their descriptions.
- Maintain a hanging indent of two or four spaces for special sections.


```python
def fetch_smalltable_rows(
    table_handle: smalltable.Table,
    keys: Sequence[bytes | str],
    require_all_keys: bool = False,
) -> Mapping[bytes, tuple[str, ...]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
          row to fetch.  String keys will be UTF-8 encoded.
        require_all_keys: If True only rows with values set for all keys will be
          returned.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. Each row is represented as a tuple of strings. For
        example:

        {b'Serak': ('Rigel VII', 'Preparer'),
         b'Zim': ('Irk', 'Invader'),
         b'Lrrr': ('Omicron Persei 8', 'Emperor')}

        Returned keys are always bytes.  If a key from the keys argument is
        missing from the dictionary, then that row was not found in the
        table (and require_all_keys must have been False).

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```


#### [Classes](https://google.github.io/styleguide/pyguide.html#384-classes)

- Classes need a docstring describing the class below the class definition.
- Document public attributes in an Attributes section, following function's Args formatting.
- Class docstrings start with a one-line summary describing the class instance.
- Exception subclasses describe the exception, not the context.
- Avoid repeating unnecessary information (e.g., stating it's a class).


```python
class SampleClass:
    """Summary of class here.

    Longer class information...
    Longer class information...

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam: bool = False):
        """Initializes the instance based on spam preference.

        Args:
          likes_spam: Defines if instance exhibits this preference.
        """
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""
```
          

#### [Block and Inline Comments](https://google.github.io/styleguide/pyguide.html#385-block-and-inline-comments)

- Comment in tricky parts of the code.
- Comment complicated operations before they start.
- Non-obvious operations get inline comments.
- Comments should start 2 spaces away from code using #, followed by at least 1 space.
- Avoid describing the code, assume reader knows Python.
        
          
```python
# We use a weighted dictionary search to find out where i is in
# the array.  We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.

if i & (i-1) == 0:  # True if i is 0 or a power of 2.
```
          

#### [Strings](https://google.github.io/styleguide/pyguide.html#310-strings)

- Use f-string, % operator, or format method for string formatting, even with all string parameters.
- Avoid using + and += for string accumulation in loops due to potential quadratic running time.

```python
# Good:
x = f'name: {name}; score: {n}'
x = '%s, %s!' % (imperative, expletive)
x = '{}, {}'.format(first, second)
x = 'name: %s; score: %d' % (name, n)
x = 'name: %(name)s; score: %(score)d' % {'name':name, 'score':n}
x = 'name: {}; score: {}'.format(name, n)
x = a + b

# Bad:
x = first + ', ' + second
x = 'name: ' + name + '; score: ' + str(n)
```

- Use ''.join on a list or io.StringIO buffer for efficient string concatenation in loops.
- Be consistent with string quote character choice (' or ") within a file.
- Prefer """ for multi-line strings over ''', except in projects with specific conventions.
- Docstrings must always use """.

#### [Error Messages](https://google.github.io/styleguide/pyguide.html#3102-error-messages)

- Precisely match error messages to actual error conditions.
- Clearly identify interpolated pieces.
- Allow simple automated processing (e.g., grepping).


### Naming Conventions

- Use `lowercase_with_underscores` for variable, function, and module names.
- Use `CAPITALIZED_WITH_UNDERSCORES` for constants.
- Use `CamelCase` for class names.
- Prefix private variables and functions with a single underscore.
- Prefix protected variables and functions with a single underscore if they are part of a public API.
          
          
```python
# Good
my_variable_name = 42

class MyClass:
    def my_public_method(self):
        pass

    def _my_private_method(self):
        pass

    def __my_special_method(self):
        pass

MY_CONSTANT_NAME = 'hello world'

# Bad - mixed case
MyVariableName = 42

# Bad - too short
a = 42

# Bad - leading underscore on public method
class MyClass:
    def _my_public_method(self):
        pass

# Bad - two leading underscores on private method
class MyClass:
    def __my_private_method(self):
        pass
```
          

### String Quotes

- Use single quotes `''` for string literals.
- Use double quotes `""` for docstrings.
          
          
```python
# Good
my_string = 'hello world'

"""This is a docstring"""

# Bad - using double quotes for string literal
my_string = "hello world"

'''This is a docstring'''
```
          

### Whitespace

- Surround binary operators with a single space on either side.
- Do not put a space after the opening parenthesis or before the closing parenthesis of a function call.
- Put a single space after a comma.
- Do not put a space before a comma.
- Put a single space after a colon and no space before the next item.
- Do not put spaces around the `=` sign when used to indicate a keyword argument or a default parameter value.


### Comments and Docstrings

- Use docstrings to document functions, classes, and modules.
- Use comments sparingly.
- Use complete sentences in docstrings and comments.
- Start the first line of a multi-line docstring with a one-line summary.
- Use triple quotes for multi-line docstrings.


### Programming Recommendations

- Use `try`-`except` blocks for exception handling.
- Use the `with` statement for file I/O.
- Use `is` and `is not` to compare with `None`.
- Use a single space after a comma in lists, tuples, and dictionaries, except for slices.
- Use list comprehensions and generator expressions to create new sequences.
- Avoid global variables.


### Imports

- Import each module on a separate line.
- Use the full module name instead of a relative import.
- Use parentheses for tuples in imports.
- Do not use wildcard imports.


### Testing

- Write unit tests for all code.
- Use the `unittest` module for writing tests.
- Use `setUp` and `tearDown` methods to set up and tear down test fixtures.
- Use `assert` statements to test expected behavior.

For more information on the Google Python Style Guide, you can visit the following link: https://google.github.io/styleguide/pyguide.html


## Docstrings
Python docstrings are used to document functions, classes, and modules. There are a few different styles for docstrings, but one of the most commonly used is the "Google Style" docstring, which uses a specific format for documenting the inputs, outputs, and behavior of a function or method.


### Function docstring
```python
def function_name(param1: type, param2: type, ...) -> return_type:
    """Brief summary of what the function does.

    Args:
        param1: Description of param1.
        param2: Description of param2.
        ...

    Returns:
        Description of the return value.

    Raises:
        ExceptionType: Description of when this exception is raised.
    """
```


### Class docstring
```python
class ClassName:
    """Brief summary of what the class does.

    Attributes:
        attr1 (type): Description of attr1.
        attr2 (type): Description of attr2.
        ...

    Methods:
        method1(param1: type, param2: type, ...) -> return_type:
            Description of method1.
        method2(param1: type, param2: type, ...) -> return_type:
            Description of method2.
        ...
    """
```


### Module docstring
```python
"""
Brief summary of what the module does.

This module provides:
- Feature 1
- Feature 2
- ...

Author: Your Name
Email: your_email@example.com
Date: Date created
"""
```


### Constants and variables
```python
"""
Module-level constants and variables.

Constants:
    MY_CONSTANT (type): Brief description of my constant.

Variables:
    my_variable (type): Brief description of my variable.
"""
```

```python
class MyClass:
    """
    Brief description of MyClass.

    Attributes:
        MY_CONSTANT (type): Brief description of my constant.
        my_variable (type): Brief description of my variable.
    """
```
