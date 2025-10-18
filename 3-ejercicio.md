## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es:
```
/var/lib/mysql
```

Ruta carpeta host:
```
C:\Users\danna\OneDrive\Calidad\ejercicio3\db
```

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Nada, esta completamente vacía

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
```
docker run -d --name mysqlCont --network net-wp -v "C:\Users\danna\OneDrive\Calidad\ejercicio3\db:/var/lib/mysql" -e MYSQL_ROOT_PASSWORD=sapitos -e MYSQL_DATABASE=bdds -e MYSQL_USER=Admin -e MYSQL_PASSWORD=Admin123 mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se encuentra llena de archivos sobre mysql, como el esquema, sys y tambien se muestra la base de datos que se creo como variable de entorno al crear el contenedor. 

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es:
```
/var/www/html/
```

Ruta carpeta host:
```
C:\Users\danna\OneDrive\Calidad\ejercicio3\www
```

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
```
docker run -d --name wordpressCont --network net-wp -p 9500:80 -v "C:\Users\danna\OneDrive\Calidad\ejercicio3\www:/var/www/html/" -e WORDPRESS_DB_HOST=mysqlCont -e WORDPRESS_DB_USER=Admin -e WORDPRESS_DB_PASSWORD=Admin123 -e WORDPRESS_DB_NAME=bdds wordpress 
```

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1919" height="1093" alt="image" src="https://github.com/user-attachments/assets/168a0074-76bf-474b-91fd-68886f54e0c2" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Al eliminar y volver a crear el contenedor, los datos del sitio se mantuvieron intactos y no cambio nada, la publicacion y el estilo asignado desde el principio se mantuvieron.
