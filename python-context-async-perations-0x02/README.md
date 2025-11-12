# Python Context & Async Database Operations

Overview
This repository demonstrates advanced Python techniques for managing SQLite connections and executing queries using class-based context managers and asynchronous programming. It contains three focused exercises:

- A class-based context manager for opening/closing database connections
- A reusable query context manager that executes parameterized queries
- Concurrent asynchronous queries using aiosqlite and asyncio.gather

Prerequisites
- Python 3.8+
- Install dependencies:
    - pip install aiosqlite

Project structure
- 0-databaseconnection.py — implement DatabaseConnection context manager; run a simple SELECT * FROM users
- 1-execute.py — implement ExecuteQuery context manager to run "SELECT * FROM users WHERE age > ?"
- 3-concurrent.py — implement async_fetch_users(), async_fetch_older_users(), and run them concurrently with asyncio.gather()
- README.md — this file

Learning objectives
- Implement class-based context managers using __enter__ and __exit__
- Ensure proper resource acquisition and automatic cleanup
- Use aiosqlite for non-blocking SQLite operations
- Run multiple asynchronous queries concurrently with asyncio.gather

How to run each exercise
1) Database connection context manager
- Purpose: create DatabaseConnection with __enter__/__exit__ to open/close a sqlite3 connection.
- Run: python 0-databaseconnection.py
- Expected: prints rows from SELECT * FROM users

2) Reusable query context manager
- Purpose: create ExecuteQuery(query, params) that opens the connection, executes the query, and returns results from __enter__.
- Query: "SELECT * FROM users WHERE age > ?"
- Params: (25,)
- Run: python 1-execute.py
- Expected: prints rows matching the condition

3) Concurrent asynchronous queries
- Purpose: use aiosqlite + asyncio to fetch multiple queries concurrently.
- Implement:
    - async_fetch_users() — fetch all users
    - async_fetch_older_users() — fetch users older than 40
    - fetch_concurrently() — call asyncio.gather(async_fetch_users(), async_fetch_older_users())
- Run: python 3-concurrent.py (the script should call asyncio.run(fetch_concurrently()))
- Expected: both result sets printed; total runtime reduced by concurrency

Tips and notes
- Use context managers to avoid connection leaks: closing connections in __exit__ even when exceptions occur.
- For async code, prefer aiosqlite for SQLite and always await connection/context manager methods.
- Keep queries parameterized to prevent SQL injection.

Assessment & submission
- Manual review will check file presence and correctness.
- Ensure you submit on time to be able to generate the review link.
- Checklist:
    - [ ] Complete implementations for 0-databaseconnection.py, 1-execute.py, 3-concurrent.py
    - [ ] Test locally
    - [ ] Submit repository and generate review link
    - [ ] Request peer reviews

Support
If you need help, run the scripts locally and inspect printed outputs and exception traces to debug resource handling or async errors.

Happy coding!
