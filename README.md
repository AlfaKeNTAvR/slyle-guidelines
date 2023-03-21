# slyle-guidelines


## Setting a Custom Git Commit Message Template
By setting a custom Git commit message template, you can ensure that your commit messages follow a consistent format and contain all the necessary information for your team or collaborators to understand the changes being made in the repository.

To set a custom Git commit message template for your repository, follow these steps:

1. Download the *git_commit_template.txt* file.

2. Move the file to a repository or to a home directory.

3. Open a terminal and set the *commit.template* configuration option to the path of the template file by using the following command:

<pre>
&emsp;git config --global commit.template /<path_to_the_template>/commit_template.txt
</pre>

Note that the *--global* option sets the configuration globally for all Git repositories on your machine. If you only want to set the configuration for the current repository, you can omit the *--global* option.

The next time you create a commit, Git will use your custom template as the default commit message. You can still modify the message as needed before finalizing the commit.


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
