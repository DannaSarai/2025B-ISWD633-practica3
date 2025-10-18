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
# COMPLETAR CON EL COMANDO
```
docker run -d --name nginxCont -p 8080:80 -v "C:\nginx\html:/usr/share/nginx/html" nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Cuando ingreso al servidor me sale un "403 Forbidden" y la version de la imagen de nginx con la que se creo, practicamente muestra que la carpeta que cree y en la que fue montada el servidor esta vacia.  

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Es reemplazado o queda oculto de cierta forma al crear el contenedor en una ruta nuestra, es decir, del host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al ingresar se puede ver montado el template que descargue de la página y se puede interactuar con esta.

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm -f nginxCont
```

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al eliminar el contenedor e ir a ver el servidor ya no se mostraba nada, cuando volvi a crear el contenedor y recargue la pagina esta me volvió a mostar el template que descargue anteriormente y pude interactuar nuevamente con esta pagina.

