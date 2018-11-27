---
title: Python code standards
description: Code style standards for Python
---

This document outlines the rules for writing Python code across all our Projects.

## Code style and formatting

All code must conform to [PEP 8](https://pep8.org/) and be formatted with [black](https://github.com/ambv/black) using the option `--line-length 79`.

Project should be configured to block merging on pull requests that do not conform to these standards.

## Testing

Although tests are lacking on many of our existing projects, writing tests is strongly encouraged. Please write tests for any new code if at all possible, and any efforts to improve test coverage on any project would be greatly appreciated.

## Documentation

You should document your functions with docstrings in accordance with [PEP 257](https://www.python.org/dev/peps/pep-0257/).
