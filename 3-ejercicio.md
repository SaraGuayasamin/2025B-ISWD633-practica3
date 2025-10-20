## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# La carpeta db del host, una vez que el contenedor MySQL ha iniciado y creado la base de datos, contiene todos los archivos binarios, datos, tablas, esquemas y configuraciones de tu base de datos MySQL. En esencia, contiene el estado persistente completo de tu servidor MySQL.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# docker run -d --name contenedor_mysql --network net-wp -v C:/ruta/absoluta/ejercicio3/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD='TuPasswordRoot' -e MYSQL_DATABASE='wordpress_db' -e MYSQL_USER='wordpress_user' -e MYSQL_PASSWORD='TuPasswordUser' mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
## [NO CONTENT FOUND]Al iniciar el contenedor de MySQL con el Al iniciar el contenedor MySQL con el comando que configuramos, y al mapear la carpeta .../ejercicio3/db a la ruta de datos interna de MySQL (/var/lib/mysql), se observa lo siguiente en la carpeta del host

La carpeta db (que estaba vacía) se llena automáticamente con la estructura de directorios y archivos de datos binarios del servidor MySQL.
### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 

