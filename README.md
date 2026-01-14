SQL INJECTION DETECTOR

- scanner.py : The main detection tool. It crawls the target URL, finds forms and query parameters, and fuzzes them with common SQL injection payloads.
- vulnerable_app.py : A Flask web application intentionally vulnerable to SQL injection (SQLite based) for testing purposes.
- requirements.txt : Dependencies ( requests , beautifulsoup4 , flask ).
### HOW TO USE
1. Install Dependencies:
 1- pip install -r f:\"YOUR FOLDER´S NAME"\sql_injection_detector\requirements.txt
   
2- Run the Scanner: You can run the scanner against any URL. For example: 
  python f:\"YOUR FOLDER´S NAME"\sql_injection_detector\scanner.py http://example.com

3- Test with Vulnerable App: To see it in action, first start the vulnerable app in one terminal:
  python f:\"YOUR FOLDER´S NAME"\sql_injection_detector\vulnerable_app.py
Then, in another terminal, run the scanner against it:
  python f:\"YOUR FOLDER´S NAME"\sql_injection_detector\scanner.py http://127.0.0.1:5000

-------------------------------------------------------------------------------------------------------
  ### Features
- Form Detection : Automatically finds all forms on a page.
- Parameter Fuzzing : Tests URL query parameters (e.g., ?id=1 ).
- Form Fuzzing : Tests input fields in forms (supports GET and POST).
- Error Detection : Identifies SQL errors from MySQL, PostgreSQL, MSSQL, Oracle, SQLite, and more.
### EXAMPLE OUTPUT
```
[*] Detected 2 forms on http://127.0.0.1:5000
  [~] Testing form to http://127.0.0.1:5000/search with 
  payload: '...
[+] SQL Injection vulnerability detected (Form)!
    Target: http://127.0.0.1:5000/search
    Database: SQLite
```
-------------------------------------------------------------------------------------------------------
You can run the following command to view the contents of test.db :

```
python f:\"YOUR FOLDER´S NAME"\sql_injection_detector\inspect_db.py
```
I've already run it, and here is the current content of your database:

```
--- Database: test.db ---

Table: users
------------
Columns: id, username, password
Data:
  (1, 'admin', 'secret')
  (2, 'user', '123456')
```
The script source code is at inspect_db.py . It connects to the SQLite database and prints all tables and their rows.
