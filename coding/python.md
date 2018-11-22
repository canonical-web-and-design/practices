---
layout: base
---

# Python code standards

This document outlines the rules for writing Python code across all our Projects.

## Code style and formatting

All Code should be written in accordance with [PEP 8](https://pep8.org/).
To correctly format all your code please use [black](https://github.com/ambv/black). Since it differs in a small way from the standard **PEP8** make sure to pass `--line-length 79` when using it. The reason for black to do this is outlined [here](https://github.com/ambv/black#line-length).

## Testing

All logic should be tested. If you add something new to the Codebase make sure that you add sufficient testing to ensure longterm maintainability of our projects.

## Documentation

Document your functions with docstrings in accordance with [PEP 257](https://www.python.org/dev/peps/pep-0257/).