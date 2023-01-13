# Odoo

 - Para instalar el Postgres primero tendremos que ver que no haya ninguna instancia del Postgres con ese puerto activado, para ello vamos a revisar 2 cosas.
 
  1. En visual studio code, en la parte de contenedores vamos a buscar que no tenemos ningun Postgres bindeado en ese puerto.
  2. En la terminal haremos sudo service postgresql stop, esto parará cualquier escucha de Postgres que tengamos en el ordenador. Si queremos revisar
     antes si hay alguna escucha haremos sudo netstat -putan |grep 5432, asi sabremos si lo anterior es necesario oh no.

 - Una vez revisado eso hacemos un docker compose yml en el que ponemos la base datos junto al usuario, contraseña y puertos a los que enlazamos el SQL.
   En este caso sera 5432 y para levantarlo haremos docker-compose up
