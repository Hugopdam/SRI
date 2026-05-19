# Actividad 1 - Instalación de Docker

Partimos de una maquina limpia, así que actualizamos el listado de paquetes con sudo apt update && sudo apt upgrade

<img width="689" height="254" alt="image" src="https://github.com/user-attachments/assets/f8152e8d-f6d1-4349-92e4-5e1c2897649f" />

Después de eso, vamos a instalar Docker usando el repositorio apt, y para ello primero tenemos que configurarlo con la clave GPG oficial. Lo hacemos así:

<img width="676" height="379" alt="image" src="https://github.com/user-attachments/assets/a4348463-352e-4f3e-951d-33aa81be43e1" />

Ahora creamos la carpeta /etc/apt/keyrings y descargamos docker ahi dentro. Usamos los siguientes comandos:

<img width="1107" height="93" alt="image" src="https://github.com/user-attachments/assets/193c16f4-0e8c-434b-989d-80974369f3d6" />

Añadimos el repositorio a apt:

 <img width="788" height="292" alt="image" src="https://github.com/user-attachments/assets/07614cd9-3b3a-4fdf-a75d-8d6644c7bdd1" />

Y usamos sudo apt update para ver que se ha agregado al repositorio apt:

<img width="746" height="196" alt="image" src="https://github.com/user-attachments/assets/2b0bdc24-f734-40ad-9f36-ff622dde830d" />

Para finalizar, instalamos la última versión de docker con:

<img width="1174" height="390" alt="image" src="https://github.com/user-attachments/assets/abac0e28-7c47-4a16-a932-83fe91434038" />

Verificamos que se ha instalado mirando la versión:

<img width="770" height="255" alt="image" src="https://github.com/user-attachments/assets/af3cf1a9-47e9-4d45-8986-941d1bec3b36" />
