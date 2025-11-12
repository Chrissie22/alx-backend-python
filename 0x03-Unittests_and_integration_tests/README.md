# Unittests and Integration Tests

## Learning Objectives

By the end of this project, you will be able to explain:

- The difference between unit and integration tests
- Common testing patterns (mocking, parametrizations, fixtures)

## Requirements

- Ubuntu 18.04 LTS with Python 3.7
- All files end with a newline
- Shebang: `#!/usr/bin/env python3`
- pycodestyle (v2.5) compliant
- All files must be executable
- Full documentation for modules, classes, and functions
- Type annotations for all functions and coroutines

## Project Structure

| File | Purpose |
|------|---------|
| `utils.py` | Utility functions for testing |
| `client.py` | GitHub client implementation |
| `fixtures.py` | Test fixtures and payloads |
| `test_utils.py` | Unit tests for utils module |
| `test_client.py` | Unit and integration tests for client |

## Tasks

| # | Title | Description |
|---|-------|-------------|
| 0 | Parameterize a unit test | Test `utils.access_nested_map` with multiple inputs |
| 1 | Test exceptions | Test `KeyError` handling in `access_nested_map` |
| 2 | Mock HTTP calls | Mock `requests.get` in `utils.get_json` |
| 3 | Parameterize and patch | Test memoization with mocked methods |
| 4 | Decorators | Test `GithubOrgClient.org` with patched `get_json` |
| 5 | Mocking properties | Test `GithubOrgClient._public_repos_url` |
| 6 | Multiple patches | Test `GithubOrgClient.public_repos` |
| 7 | Parametrize tests | Test `GithubOrgClient.has_license` with fixtures |
| 8 | Integration tests | Full integration test with `parameterized_class` |

