# Actividad 4 - Almacenamiento y redes Docker
## Despliegue de la aplicación Guestbook
Primero creamos la red interna de Docker:

<img width="711" height="57" alt="image" src="https://github.com/user-attachments/assets/b2273964-188f-44f8-bc66-a5d6f33fcfa7" />

Ahora ejecutamos los dos contenedores de los dos servicios necesarios. Vemos que el flag -v nos da un volumen persistente:

<img width="1252" height="617" alt="image" src="https://github.com/user-attachments/assets/17f13ba3-d6ae-405f-9447-828e7257600f" />

Comprobamos que la aplicacion está funcionando con la IP del WSL:

<img width="926" height="338" alt="image" src="https://github.com/user-attachments/assets/91a7fed7-7eb3-45b5-bbf0-76b455465caa" />

## Despliegue de la aplicación Temperaturas
Como antes, vamos a crear una red para conectar los dos contenedores:

<img width="731" height="62" alt="image" src="https://github.com/user-attachments/assets/527b9bde-73e3-43b4-8294-ff1d65989091" />

Y nos descargamos el frontend y el backend de la aplicación:

<img width="1235" height="306" alt="image" src="https://github.com/user-attachments/assets/c89d1bc9-8ef7-44ab-9de0-d3074ff761dd" />

Comprobamos: 

<img width="1082" height="449" alt="image" src="https://github.com/user-attachments/assets/b1c7afb0-7c84-4d6b-8095-410625fd0d4d" />

# Despliegue de Wordpress + mariadb
Creamos la red:

<img width="593" height="60" alt="image" src="https://github.com/user-attachments/assets/189ace44-320f-48c0-9d3e-b8140d54705c" />

Y creamos los contenedores de mariaDB y wordpress:

<img width="936" height="237" alt="image" src="https://github.com/user-attachments/assets/d3ef84db-9ce9-4659-896d-eae351b69dfb" />

<img width="1251" height="642" alt="image" src="https://github.com/user-attachments/assets/1fc1c6e0-5e79-48c1-96cf-031ab57bc457" />

Lo comprobamos:

<img width="822" height="442" alt="image" src="https://github.com/user-attachments/assets/7c781f00-288d-4a35-bb3d-7d93c4b0b031" />
