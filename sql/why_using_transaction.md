# Why using Transaction
================================

**Author**: Lien Chen  **Date**: 2020-08-17

In sql, sometimes we have some commands that need multiple sql commands to run.
To ensure all commands work successfully, if a commands or more failure, it can let all commands to unsuccess.
We will use transaction to ensure this full transaction.
All transaction must be atomic, consistent, isolated and durable.

[reference](https://www.w3resource.com/sql/controlling-transactions.php)