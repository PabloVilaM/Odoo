## Odoo

# Primero vamos a revisar las partes del Docker-compose

 - El docker compose esta dividido en 2 servicios la base de datos y el odoo. 
    - La database estará compuesto de:
     - La imagen (la versión de postgres que descargamos o se descará al hacerlo).
     - El nombre del contenedor que queremos ponerle.
     - El restart es opcional, solo hará que cada vez que iniciemos el ordenador se reinicie.
     - El environment contendrá variables de la propia bd: En este caso el log para el usuario, la contraseña y la DB.
     - Los puertos, que siendo postgres lo bindearemos al 5432.
     - El volumen, tambien opcional pero viene bien saber donde se guarda la información y tenerlo en "físico".
    - El Odoo tendrá 4 partes simples:
     - La imagen (la versión de odoo que queremos, la version 16.0 o latest)
     - El nombre del contenedor
     - Los puertos, que en este caso usaremos el 8069.
     - Y opcional, pero bueno ponerlo es que depende del otro servicio, la database. Puesto que Odoo necesitá tener la base de datos iniciada.

# Para configurar el Postgres primero tendremos que ver que no haya ninguna instancia del Postgres con ese puerto activado, para ello vamos a revisar 2 cosas.
 
  1. En visual studio code, en la parte de contenedores vamos a buscar que no tenemos ningun Postgres bindeado en ese puerto.
  2. En la terminal haremos sudo service postgresql stop, esto parará cualquier escucha de Postgres que tengamos en el ordenador. Si queremos revisar
     antes si hay alguna escucha haremos sudo netstat -putan |grep 5432, asi sabremos si lo anterior es necesario oh no.

 - Una vez hecho todo esto, podemos hacer el docker-compose up y con ello lanzaremos el odoo con la base de datos correspondientes. Esto nos llevará al proximo paso.

# Enlazar Postgres y Odoo
 
  - Habiendo hecho ya los pasos previos poco queda sobre este paso. Una vez levantemos odoo, lo abramos en el navegador nos saldrá la primera pestaña inicial en el que habrá que rellenar unos datos básicos y crear una db de test. Llevandonos a tenerlo ya preparado pero faltando enlazar el IDE con la base de datos.

# Enlazar PyCharm con la Base de datos

 - Recordamos el environment que establecimos en el primer paso? Bien. Iremos al PyCharm Professional (porque el community no tiene esta feature) y iremos a la derecha donde veremos que hay una pestaña de Database. Clickamos en ella y le damos al simbolo de "+". Seleccionamos el PostgresSQL y ponemos los datos de acceso puestos en el primer paso. Podemos usar el Test Connection para comprobar si lo hemos hecho correctamente y si es así darle al Apply, entonces nos saldrá en esa zona las tablas y todo lo que contiene.
