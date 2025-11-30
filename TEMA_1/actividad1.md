# Instalación Apache

**Con una maquina ubuntu limpia y actualizada (sudo apt update && upgrade) haremos los siguientes pasos:**

Para instalar apache pondremos este comando:
<img width="879" height="243" alt="image" src="https://github.com/user-attachments/assets/f58b5672-4252-493e-ad68-c56b81f7a3cd" />

Y si ahora nos vamos a internet y ponemos localhost, veremos que se nos ha instalado correctamente:
<img width="911" height="514" alt="image" src="https://github.com/user-attachments/assets/5760d6bd-9236-469e-8c01-90839da83828" />

Ahora para instalar mysql pondremos el seguiente comando:
<img width="1193" height="431" alt="image" src="https://github.com/user-attachments/assets/4f6193bd-5d0b-41db-93a5-606ea90d1c97" />

Le damos a  que si esperamos a que se instale. Ahora,mejecutaremos una secuencia preestablecida de comandos de seguridad que eliminará algunos ajustes predeterminados poco seguros y se bloqueará el acceso a su sistema de base de datos:
<img width="865" height="239" alt="image" src="https://github.com/user-attachments/assets/0f6e37e3-9f0b-4304-b5be-bff6cc71ce63" />

Y para comprobar que lo hemos instalado bien lo probamos:
<img width="786" height="297" alt="image" src="https://github.com/user-attachments/assets/41cb47c9-49a6-45cd-afd6-4bc296ab3a09" />

Ahora vamos a instalarr PHP. Lo haremos con este comnando:
<img width="1200" height="411" alt="image" src="https://github.com/user-attachments/assets/55d57420-00a7-43c3-aed2-1002411da2dd" />

Para comprobar que la instalación es correcta, miramos su versión:
<img width="755" height="130" alt="image" src="https://github.com/user-attachments/assets/8bd687c6-09fc-401f-a72d-c6ff0698d047" />

Ahora tenemos una maquina LAMP (linux apache mysql php)  
El siguiente paso es crear un host virtual para nuestro sitio web. Para ello vamos a crear una estructura de dominio dentro de /var/www/ con el nombre mi_domi. Vamos a aprovechar y cambiarle el propietario a nuestro usuario a la misma vez:
<img width="1037" height="93" alt="image" src="https://github.com/user-attachments/assets/2cba4d9c-a091-45d8-9a80-43486eb51289" />

Vamos a crear un nuevo archivo en ‘sites-available’ de Apache usando nano, que servirá como archivo de configuración de nuestro dominio:
<img width="861" height="194" alt="image" src="https://github.com/user-attachments/assets/ae141a17-2029-4dc6-b42d-55f5594fee39" />

Ahora habilitamos el nuevo host virtual y reiniciamos apache:
<img width="884" height="245" alt="image" src="https://github.com/user-attachments/assets/1dc97ccb-33aa-4e7c-ba1e-189fec60a64f" />

Y si probamos en internet veremos que funciona:
<img width="485" height="206" alt="image" src="https://github.com/user-attachments/assets/5f907cb8-6260-4371-b8f8-0eabcc15c53c" />

Ahora vamos a probar que nuestra nueva página web pueda procesar peticiones PHP. Para ello creamos un nuevo archivo llamado info.php dentro de la carpeta mi_domi con este código:
<img width="812" height="91" alt="image" src="https://github.com/user-attachments/assets/f34ff287-af64-4cec-8805-78e49d3d3ff5" />

Y ahora nos vamos a mi_domi/info.php:
<img width="1088" height="556" alt="image" src="https://github.com/user-attachments/assets/82ec80ba-76c6-402f-a6e6-aaf82235bcdc" />
