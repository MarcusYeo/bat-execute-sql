@echo off
setlocal

set LOG_FILE=execution_log.txt

echo ========= Start scripts =========
echo ========= Start scripts ========= >> %LOG_FILE%

call :MyFunction myFolder myServer myDatabase myUser myPassword
:: call :MyFunction myFolder myServer myDatabase myUser myPassword

echo ========= End scripts =========
echo ========= End scripts ========= >> %LOG_FILE%

pause
exit /b

:: --- Function Definition ---
:MyFunction
:: %1 is the first argument passed, %2 is the second argument, etc.
if "%1"=="" (
    echo Error: No folder specified! >> %LOG_FILE%
    echo Error: No folder specified!
    exit /b
)
if "%2"=="" (
    echo Error: No server specified! >> %LOG_FILE%
    echo Error: No server specified!
    exit /b
)
if "%3"=="" (
    echo Error: No database specified! >> %LOG_FILE%
    echo Error: No database specified!
    exit /b
)
if "%4"=="" (
    echo Error: No user specified! >> %LOG_FILE%
    echo Error: No user specified!
    exit /b
)
if "%5"=="" (
    echo Error: No password specified! >> %LOG_FILE%
    echo Error: No password specified!
    exit /b
)

set FOLDER=%~dp0%1
set SERVER=%2
set DATABASE=%3
set USER=%4
set PASSWORD=%5

:: Remove trailing backslash if present
set FOLDER=%FOLDER:\\=\%

:: Debug: Print out the passed arguments for troubleshooting
echo Folder = %FOLDER% >> %LOG_FILE%
echo Server = %SERVER% >> %LOG_FILE%
echo Database = %DATABASE% >> %LOG_FILE%
echo User = %USER% >> %LOG_FILE%

echo === Running scripts on %DATABASE% with server %SERVER% ===
echo === Running scripts on %DATABASE% with server %SERVER% === >> %LOG_FILE%

:: Check if the folder exists
if not exist "%FOLDER%" (
    echo Error: Folder %FOLDER% does not exist! >> %LOG_FILE%
    echo Error: Folder %FOLDER% does not exist!
    exit /b
)

:: Check for SQL files
if not exist "%FOLDER%\*.sql" (
    echo Error: No SQL files found in folder %FOLDER% >> %LOG_FILE%
    echo Error: No SQL files found in folder %FOLDER%
    dir "%FOLDER%" >> %LOG_FILE%
    exit /b
)

:: Execute SQL scripts in the folder
for %%F in ("%FOLDER%\*.sql") do (
    echo Executing %%F
    echo Executing %%F >> %LOG_FILE%
    sqlcmd -S %SERVER% -d %DATABASE% -U %USER% -P %PASSWORD% -i "%%F" >> %LOG_FILE%
)

goto :EOF
