# bat-execute-sql
Bat SQL Script Executor

A Windows batch script designed to automate the execution of SQL scripts stored across multiple folders in a specified directory. The script sequentially runs .sql files in order, ensuring that all scripts are executed against a specified SQL Server database. Ideal for running batch SQL operations such as database migrations, data transformations, or maintenance tasks.


Add more lines on for more folders

call :MyFunction [folder] [server] [database] [user] [password]
