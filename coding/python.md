* * *

title: Python code standards
description: Code style standards for Python

* * *

This document outlines the rules for writing Python code across all our Projects.

## Code style and formatting

We use three tools to conform to [PEP 8](https://pep8.org/):

-   [Black](https://black.readthedocs.io/en/stable/). We format our Python code using the option `--line-length 79` followed by the folders that we want to format. E.g. `black --line-length 79 webapp tests`

-   [Flake8](https://flake8.pycqa.org/en/latest/) is a tool to enforce code styling. It will suggest you to remove unsued variables, remove unused imports, enforce more strict whitespace practices and calculate your code complexity. E.g. `flake8 webapp tests`

-   [iSort](https://readthedocs.org/projects/isort/) automatically rearranges your imports in different sections. It separates `import package` from `from pacakage import module` and tides up the spacing between them.

Project should be configured to block merging on pull requests that do not conform to these standards. You can do this by adding the initials `WIP` to the beginning of your PR title.

> If you use VSCode, linting is enabled by default with the Python extension. To use black specifically add `"python.formatting.blackArgs": [ "--line-length", "79"], "python.formatting.provider": "black",` to your `settings.json`. Also you might want to install iSort extension and use Shift + Control (Command on a Mac) and type iSort to automatically order your imports. 

## Testing

Although tests are lacking on many of our existing projects, writing tests is strongly encouraged. 

-   We write our tests in the `tests` folders. Files usually follow the `test_*.py` convention. 
-   After a tests has been written, we use the `python -m unittest discover` to run the tests.
-   Once the tests are run successfuly, you should check the coverage report by running `coverage report -m` to check that you have passed the minimum required code coverage level to avoid failing Circle CI tests.

Please write tests for any new code if at all possible, and any efforts to improve test coverage on any project would be greatly appreciated.

## Documentation

You should document your functions with docstrings in accordance with [PEP 257](https://www.python.org/dev/peps/pep-0257/).