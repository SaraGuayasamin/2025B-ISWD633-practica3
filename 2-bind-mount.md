# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# docker run -d --name mi_servidor_nginx -p 80:80 -v "C:\Users\Usuario\Desktop\nginx\html:/usr/share/nginx/html" nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
<img width="512" height="153" alt="image" src="https://github.com/user-attachments/assets/0ae04fd5-bb7c-44d1-9d64-8fd1186534f8" />

# Al ingresar al servidor de Nginx y recibir el error "403 Forbidden", significa que el servidor te está negando el acceso al recurso solicitado (generalmente el directorio raíz). Esto sucede porque Nginx no puede leer los archivos en la carpeta mapeada o no encuentra el archivo principal (index.html) que debe servir por defecto.

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
# El archivo index.html que venía originalmente en la imagen de Nginx dentro del contenedor ha sido reemplazado o "escondido" por la carpeta local al usar el mapeo de volumen.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
## ya aparece la pagina en html en el localhost 
<img width="1472" height="857" alt="image" src="https://github.com/user-attachments/assets/df4d9be0-a11e-445e-a356-ee797ff1e657" />


### Eliminar el contenedor
# docker rm mi_servidor_nginx

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# ya no se abre la pagina con html a pesar que el documento está dentro de la carpeta y esto se debe a que eliminamos el contenedor
<img width="945" height="664" alt="image" src="https://github.com/user-attachments/assets/b509fd38-b265-429d-aea9-38d5dbfb7574" />



