# Laboratorio Docker
### Ejercicio 1, Paso 1
Creamos el contenedor, con acceso directo a la consola, añadiendo el parámetro -it, y comprobamos que curl no está instalado.
<img width="732" height="155" alt="image" src="https://github.com/user-attachments/assets/1a2ef491-3049-4d70-9767-e160ef9cd101" />
Tras ejecutar los comandos indicados en el ejercicio, vuelvo a hacer un curl --version y ya se puede comprobar que curl está instalado.
<img width="1094" height="169" alt="image" src="https://github.com/user-attachments/assets/ef21c949-9354-4f16-b6e7-7ded0c259cdb" />
Para crear una nueva imagen con los cambios del contenedor se utiliza docker commit, tal y como se puede ver en la captura.
<img width="748" height="247" alt="image" src="https://github.com/user-attachments/assets/9f5100d6-0dab-4185-891b-98f0c1c51c9a" />
### Ejercicio 1, Paso 2
Tras crear un Dockerfile en mi carpeta actual, con las dos líneas que indica el Paso 2, construyo la imagen y ejecuto el contenedor siguiendo los pasos de la siguiente captura.
<img width="1094" height="533" alt="image" src="https://github.com/user-attachments/assets/58a5dde3-5d74-4311-9c9d-4a016ab2b5e3" />
Para ver las capas de la imagen, tan solo habría que ejecutar el siguiente comando.
<img width="1015" height="173" alt="image" src="https://github.com/user-attachments/assets/02088494-9435-4dce-9726-708324153e18" />
### Ejercicio 2
Creo un Dockerfile con un simple `FROM ubuntu` y construyo la imagen: `docker build -t limpieza:v1 .`
Después añado la siguiente línea al dockerfile: `RUN apt-get update && apt-get install -y curl` y vuelvo a construir: `docker build -t limpieza:v2 .`
Por último, modifico la línea anteriormente creada para añadirle wget: `RUN apt-get update && apt-get install -y curl wget` y vuelvo a construir: `docker build -t limpieza:v3 .`
Quedando mis imágenes como en la captura siguiente.
<img width="754" height="286" alt="image" src="https://github.com/user-attachments/assets/9be1be8c-20de-4829-9915-c70125638a7e" />
El resultado que se puede ver es que con cada build se crea una nueva versión de la imagen, ocupando espacio en disco. Se podrían borrar con el comando `docker rmi limpieza:v1 limpieza:v2`
### Ejercicio 3
Ejecuto el contenedor, creando un nuevo volumen con el siguiente comando: `docker run -d --name pg -e POSTGRES_PASSWORD=0010 -v pgdata:/var/lib/postgresql postgres`
Me conecto, creo la tabla e inserto un registro del siguiente modo, según la captura.
<img width="565" height="382" alt="image" src="https://github.com/user-attachments/assets/a4f31ae0-4b04-496a-a9eb-97ec88e09722" />
Detengo y elimino el contenedor: `docker stop pg` y `docker rm pg`
Creo el nuevo contenedor, pero el volumen ya existe, porque no ha sido borrado: `docker run -d --name pg2 -e POSTGRES_PASSWORD=0010 -v pgdata:/var/lib/postgresql postgres`
Compruebo que los datos siguen existiendo.
<img width="1075" height="286" alt="image" src="https://github.com/user-attachments/assets/2b69a9d1-3576-47e8-8f5e-2d88232674ac" />
### Ejercicio 4
Creo el fichero index.html en una carpeta local de mi máquina e inicio el contenedor de este modo: `docker run -d --name nginx -p 80:80 -v ${PWD}/index.html:/usr/share/nginx/html/index.html nginx`
Al abrir localhost se puede ver el resultado correctamente.
<img width="320" height="140" alt="image" src="https://github.com/user-attachments/assets/7f4a2b00-7fac-4f32-b4c6-adc727b06fc5" />
Si modifico mi archivo localmente, el cambio aparece de inmediato en el contenedor, como se puede apreciar en la captura siguiente.
<img width="368" height="159" alt="image" src="https://github.com/user-attachments/assets/1153ae0a-dead-496d-aeef-e30c256f2e4c" />
### Ejercicio 5
Con el comando `docker volume ls` puedo ver todos los volumenes creados. Ahora puedo inspeccionar un volumen cualquiera, por ejemplo pgdata, y comprobar toda su información, incluyendo el "Mountpoint", que es donde se guardan los datos. Ver siguiente captura.
<img width="675" height="346" alt="image" src="https://github.com/user-attachments/assets/5f63388e-981c-49ea-bb1c-5a08cee3993a" />

