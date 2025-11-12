# Python Decorators — Database Utilities

Project that teaches how to use Python decorators to augment database operations (logging, connection management, transactions, retries, caching). Each task is a focused exercise that builds a reusable decorator to simplify common DB patterns.

## Learning objectives
- Deepen understanding of Python decorators for reusable, expressive code.
- Automate connection handling, logging, and transaction management.
- Add resilience (retry) and performance (caching) to DB operations.
- Apply best practices for maintainable, testable DB interaction.

## Requirements
- Python 3.8+
- SQLite3 (a `users` table for testing)
- Familiarity with decorators, sqlite3, Git/GitHub

## Tasks (summary)

Task 0 — Logging database queries  
- Objective: Create a `log_queries` decorator to log SQL before execution.  
- Prototype:
```python
import sqlite3
import functools

def log_queries():
    """Decorator that logs SQL queries before executing the wrapped function."""
    # implement
```
- File: 0-log_queries.py

Task 1 — Database connection decorator  
- Objective: Create `with_db_connection` to open a connection, pass it to the function, and close it after.  
- Prototype:
```python
import sqlite3
import functools

def with_db_connection(func):
    """Open sqlite3 connection, pass as first arg, close after."""
    # implement
```
- File: 1-with_db_connection.py

Task 2 — Transaction management decorator  
- Objective: Implement `transactional` that commits on success and rollbacks on exceptions. Reuse `with_db_connection`.  
- Prototype:
```python
import sqlite3
import functools

# include with_db_connection
def transactional(func):
    """Wrap DB operations in a transaction (commit or rollback)."""
    # implement
```
- File: 2-transactional.py

Task 3 — Retry on failure decorator  
- Objective: Implement `retry_on_failure(retries=3, delay=2)` to retry transient failures. Reuse `with_db_connection`.  
- Prototype:
```python
import time
import sqlite3
import functools

def retry_on_failure(retries=3, delay=2):
    """Retry the wrapped function up to `retries` times with `delay` seconds."""
    # implement
```
- File: 3-retry_on_failure.py

Task 4 — Query result caching decorator  
- Objective: Implement `cache_query` to cache results keyed by SQL query string. Reuse `with_db_connection`.  
- Prototype:
```python
import time
import sqlite3
import functools

query_cache = {}

def cache_query(func):
    """Cache query results based on the SQL string argument."""
    # implement
```
- File: 4-cache_query.py

Task 5 — Manual review  
- Project will be manually reviewed; ensure files are present, tests/usage are documented, and a review link is generated before deadline.

## Testing and usage
- Create an SQLite `users.db` with a `users` table for local testing.
- Implement each decorator in its corresponding file and run the provided example calls.
- Follow repository structure:
  - Repo: alx-backend-python
  - Directory: python-decorators-0x01

## Notes
- Keep decorators generic and well-documented.
- Ensure connections are always closed and transactions maintain consistency.
- Use small, deterministic tests to validate behavior (success, failure, retry, cache hits).

Happy coding!
