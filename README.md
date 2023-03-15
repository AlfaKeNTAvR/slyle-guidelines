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

- [Indentation](#indentation)
- [Line Length](#line-length)
- [Naming Conventions](#naming-conventions)
- [String Quotes](#string-quotes)
- [Whitespace](#whitespace)
- [Comments and Docstrings](#comments-and-docstrings)
- [Programming Recommendations](#programming-recommendations)
- [Imports](#imports)
- [Testing](#testing)

### Indentation

- Use 4 spaces for indentation.
- Do not use tabs or mix tabs and spaces.
- Align the closing parentheses with the start of the line that contains the corresponding opening parentheses.
- *how to configure this in VScode*

### Line Length

- Limit lines to a maximum of 79 characters.
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
