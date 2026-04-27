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

