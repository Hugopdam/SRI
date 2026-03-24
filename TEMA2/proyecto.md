# Práctica 2º Trimestre - Servidor de Alojamiento Web
## Pasos previos:
Para esta practica necesitamos una maquina virtual en proxmox con Ubuntu 24.04LTS y le daremos una IP estática:
<img width="724" height="537" alt="image" src="https://github.com/user-attachments/assets/559b79aa-f7b4-40ac-8bad-813329cf1fd0" />
<img width="712" height="536" alt="image" src="https://github.com/user-attachments/assets/05077d6e-eea7-4ce7-a3b7-5ff46c8c4a0f" />

Una vez hecho esto, vamos a instalar el sistema operativo, parándonos en dos puntos clave:
En Network configuration le asiganremos una IP estática:
<img width="1267" height="276" alt="image" src="https://github.com/user-attachments/assets/be96e99c-e171-4362-a59e-cbfca0d00e4d" />
Y ponemos la ip dentro de la subnet del proxmox que nosotros prefiramos:
<img width="582" height="377" alt="image" src="https://github.com/user-attachments/assets/230ebe1e-f913-4993-899f-2e012f5cd2f9" />

Lo siguiente es configurar el perfil del administrador del sistema, de este modo:

<img width="1262" height="340" alt="image" src="https://github.com/user-attachments/assets/3fd8683e-7e55-4252-a571-49502264665d" />

Por último, dejamos activo ya el servidor SSH:
<img width="1255" height="294" alt="image" src="https://github.com/user-attachments/assets/c13e3177-65b0-498a-be9a-4b9598a10ba1" />

Ya lo dejamos instalarse y cuando acabe, actualizaremos los repositorios para hacer la snapshot.

## 2. Configuración del entorno base del servidor

En esta fase incorporaremos todo el software requerido para llevar a cabo la práctica. A continuación se detalla el listado de las herramientas necesarias, organizadas según el rol que desempeñan, junto con el motivo de su instalación:

### Servicios Web y entorno PHP
* **apache2:** Actuará como nuestro servidor web principal. Es una herramienta estándar del sector que ya hemos manejado extensamente durante el curso.
* **php y libapache2-mod-php:** Son los componentes esenciales para soportar contenido web dinámico. Aportan tanto el intérprete del lenguaje PHP como el módulo que habilita a Apache para procesar y traducir este código antes de mandarlo al navegador del usuario.
* **php-mysql:** Es el puente o conector necesario para que los portales creados en PHP (incluyendo la herramienta phpMyAdmin) puedan enlazarse y extraer información de nuestras bases de datos MariaDB o MySQL.

### Gestión de Bases de Datos
* **mariadb-server:** El sistema gestor de bases de datos relacionales que utilizaremos como motor principal, el cual funciona como una alternativa 100% compatible con MySQL.
* **phpmyadmin:** Plataforma web con entorno gráfico (desarrollada en PHP) que nos facilitará la administración de nuestras bases de datos directamente desde el navegador. Es una herramienta que ya hemos utilizado en el módulo de IAW.

### Transferencia de Archivos (FTP)
* **vsftpd:** Corresponde a las siglas de *Very Secure FTP Daemon*. Es el servicio encargado de gestionar el tráfico de archivos, permitiendo a los distintos clientes alojar, subir o descargar el contenido de sus proyectos web en sus respectivos directorios del servidor.

### Sistema de Nombres de Dominio (DNS)
* **bind9 (y sus paquetes dependientes):** Es el servidor DNS que ya hemos implementado anteriormente. Lo utilizaremos para generar subdominios y administrar las zonas de resolución directa e inversa. Su misión principal será traducir direcciones legibles por humanos (como `cliente1.midominio.local`) a la dirección IP de nuestra máquina (por ejemplo, `192.168.193.110`).

### Soporte de Python para Web
* **python3 y libapache2-mod-wsgi-py3:** Proporcionan la interfaz WSGI (*Web Server Gateway Interface*). Se trata del estándar que permite a Apache enrutar y gestionar peticiones web directamente hacia aplicaciones o scripts programados en Python, garantizando un funcionamiento seguro y optimizado.

Lo vamos a instalar todo en un solo comando, que va a quedar algo larguillo:
~~~
sudo apt install apache2 php libapache2-mod-php php-mysql mariadb-server phpmyadmin vsftpd bind9 bind9utils dnsutils python3 libapache2-mod-wsgi-py3 -y
~~~~
Cuando llegue a la parte de phpmyadmin tendremos que configurarlo correctamente, primero eligiendo apache2:
<img width="900" height="234" alt="image" src="https://github.com/user-attachments/assets/ca2d3b26-e491-47bc-9d20-a1043aced429" />

Después nos pedirá configurar la base de datos de phpmyadmin:
<img width="1240" height="265" alt="image" src="https://github.com/user-attachments/assets/679a4fbb-55d2-437b-9249-fc4bc6b4bf84" />

Necesitaremos ponerle una contraseña:
<img width="1232" height="204" alt="image" src="https://github.com/user-attachments/assets/e2061b4b-69df-4b70-ba4e-5f1d73ac8b2f" />

Y ya vemos que se crea correctamente y todos los paquetes se han instalado:
<img width="736" height="350" alt="image" src="https://github.com/user-attachments/assets/f6a9f670-5a9b-46e1-8b79-84747558d44a" />

Ahora unas comprobaciones de ultima hora:
<img width="712" height="277" alt="image" src="https://github.com/user-attachments/assets/465cb87d-3791-4cad-b4ad-b5709ae9f04a" />
<img width="706" height="195" alt="image" src="https://github.com/user-attachments/assets/f8f2d170-8563-48af-86d5-f4796c99905f" />


