DETECTOR DE SQL INJECTION
scanner.py: A ferramenta principal de detecção. Ela rastreia a URL alvo, encontra formulários e parâmetros de consulta, e os testa com payloads comuns de injeção SQL.

vulnerable_app.py: Uma aplicação web Flask intencionalmente vulnerável a injeção SQL (baseada em SQLite) para fins de teste.

requirements.txt: Dependências (requests, beautifulsoup4, flask).

COMO USAR
1. Instalar Dependências:

1- pip install -r f:"NOME DA SUA PASTA"\sql_injection_detector\requirements.txt

2- Executar o Scanner: Você pode executar o scanner contra qualquer URL. Por exemplo:

  python f:"NOME DA SUA PASTA"\sql_injection_detector\scanner.py http://example.com

3- Testar com o App Vulnerável: Para vê-lo em ação, primeiro inicie o app vulnerável em um terminal:
  python f:"NOME DA SUA PASTA"\sql_injection_detector\vulnerable_app.py
Então, em outro terminal, execute o scanner contra ele:
  python f:"NOME DA SUA PASTA"\sql_injection_detector\scanner.py http://127.0.0.1:5000
  
### Recursos
Detecção de Formulários: Encontra automaticamente todos os formulários em uma página.
Fuzzing de Parâmetros: Testa parâmetros de consulta de URL (ex: ?id=1).
Fuzzing de Formulários: Testa campos de entrada em formulários (suporta GET e POST).
Detecção de Erros: Identifica erros SQL de MySQL, PostgreSQL, MSSQL, Oracle, SQLite e mais.
EXEMPLO DE SAÍDA
[*] Detected 2 forms on http://127.0.0.1:5000
  [~] Testing form to http://127.0.0.1:5000/search with 
  payload: '...
[+] SQL Injection vulnerability detected (Form)!
    Target: http://127.0.0.1:5000/search
    Database: SQLite
Você pode executar o seguinte comando para visualizar o conteúdo de test.db:
  python f:"NOME DA SUA PASTA"\sql_injection_detector\inspect_db.py
  
Eu já executei, e aqui está o conteúdo atual do seu banco de dados:
--- Database: test.db ---

Table: users
------------
Columns: id, username, password
Data:
  (1, 'admin', 'secret')
  (2, 'user', '123456')
  
O código-fonte do script está em inspect_db.py. Ele se conecta ao banco de dados SQLite e imprime todas as tabelas e suas linhas.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
ENGLISH INSTRUCTIONS

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
