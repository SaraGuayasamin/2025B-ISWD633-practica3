## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: 
C:\Users\Usuario\Desktop\ejercicio3\bd

### ¿Qué contiene la carpeta db del host?
# La carpeta db del host, una vez que el contenedor MySQL ha iniciado y creado la base de datos, contiene todos los archivos binarios, datos, tablas, esquemas y configuraciones de tu base de datos MySQL. En esencia, contiene el estado persistente completo de tu servidor MySQL.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# docker run -d --name db-mysql --network net-wp -v C:\Users\Usuario\Desktop\ejercicio3\bd:/var/lib/mysql -e MYSQL_ROOT_PASSWORD="TuPasswordRoot" -e MYSQL_DATABASE="wordpress_db" -e MYSQL_USER="wordpress_user" -e MYSQL_PASSWORD="TuPasswordUser" mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
<img width="900" height="830" alt="image" src="https://github.com/user-attachments/assets/42aa6283-0d48-44f6-9b9a-f1cd0a73f653" />
## Al haber montado un volumen para tu contenedor de MySQL usando la ruta del host C:\Users\Usuario\Desktop\ejercicio3\bd y luego iniciar el contenedor con la imagen mysql:8, la carpeta db que estaba inicialmente vacía ahora contendrá la estructura de datos y archivos binarios que MySQL necesita para funcionar.


### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# docker run -d --name wordpress --network net-wp -p 8080:80 -v C:\Users\Usuario\Desktop\ejercicio3\www:/var/www/html -e WORDPRESS_DB_HOST=db-mysql -e WORDPRESS_DB_USER="wordpress_user" -e WORDPRESS_DB_PASSWORD="TuPasswordUser" -e WORDPRESS_DB_NAME="wordpress_db" wordpress:latest

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1919" height="815" alt="image" src="https://github.com/user-attachments/assets/0d84fb6d-4aea-49f5-bfad-41eda02da9d1" />
<img width="1900" height="912" alt="image" src="https://github.com/user-attachments/assets/e6084b77-0c22-4202-9108-f1cd7608d11e" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
## Si eliminas el contenedor wordpress y lo vuelves a crear con el mismo bind mount, los archivos persistentes (archivos de WordPress y cualquier contenido almacenado en el directorio montado) permanecerán en la carpeta C:\Users\INTEL\Documents\ejercicio3\www del host. La base de datos persiste en C:\Users\INTEL\Documents\ejercicio3\db. Por tanto la configuración y el contenido (entradas, medios) deberían seguir disponibles al recrear los contenedores, siempre que montes las mismas carpetas y uses las mismas credenciales/DB.
<img width="1766" height="909" alt="image" src="https://github.com/user-attachments/assets/1a40a25e-8c8e-457a-9a4b-5707e015123a" />


