[Link para os scripts criado]()

# Instalação

Primeiro, é preciso instalar a biblioteca pyodbc. 

Podemos fazer isso usando o pip, o gerenciador de pacotes do Python. 

Por exemplo: 
~~~
pip install pyodbc
~~~~

# Conexão com o banco de dados

É preciso estabelecer uma conexão com o banco de dados usando o DSN (Data Source Name) ou uma string de conexão que contenha informações sobre o banco de dados, como o driver, o servidor, o nome do banco de dados, etc. 

Aqui está um exemplo de conexão usando um DSN:
~~~
import pyodbc
conn = pyodbc.connect('DSN=MyDSN;UID=myuser;PWD=mypassword')
~~~