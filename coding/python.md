---
title: Python code standards
description: Code style standards for Python
---

This document outlines the rules for writing Python code across all our Projects.

## Code style and formatting

We use [Flake8](https://flake8.pycqa.org/en/latest/) to check our code for compliance with [PEP 8](https://pep8.org/), e.g. with `flake8 webapp tests`. See [the list of Flake8 violations](https://flake8.pycqa.org/en/latest/user/error-codes.html) for more information.

We use [Black](https://black.readthedocs.io/en/stable/) to format our Python code using the option `--line-length 79` followed by the folders that we want to format. E.g. `black --line-length 79 webapp tests`

Optionally, you can use [iSort](https://readthedocs.org/projects/isort/) to automatically rearranges your imports in different sections. It separates `import package` from `from pacakage import module` and tides up the spaces between them. However, this is not enforced by PEP8 guidelines.

Projects should be configured to block merging on pull requests that do not conform to these standards.

## Testing

Writing tests is strongly encouraged.

- We write our tests in the `tests` folders. Files usually follow the `test_*.py` (pattern for unittest discovery)[https://docs.python.org/3/library/unittest.html#cmdoption-unittest-discover-p].
- After a tests have been written, we use the `python3 -m unittest discover --start-directory tests` to run them.
- Once the tests are run successfully, you can check the coverage report by running `coverage report -m` to check that you have passed the minimum required level to avoid failing CI tests.

Please write tests for any new code if at all possible, and any efforts to improve test coverage on any project would be greatly appreciated.

## Documentation

You should document your functions with docstrings in accordance with [PEP 257](https://www.python.org/dev/peps/pep-0257/).
