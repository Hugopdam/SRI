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
<img width="704" height="217" alt="image" src="https://github.com/user-attachments/assets/10758b42-307e-4d9d-a312-38bd8fbff54b" />
<img width="980" height="367" alt="image" src="https://github.com/user-attachments/assets/9d7ff81a-3089-489e-9abe-fc18f0ccba62" />

# 3 Configuración
Ahora vamos a dejar todo preparado para el script, y solo tengamos que añadir los usuarios y no configurar nada desde cero. Haremos lo siguiente:

### 3.1 asegurar FTP por certificados:
Vamos a hacer que el acceso FTP configure adecuadamente TLS: esto convierte el FTP normal, que es inseguro, en FTPS, cifrando las contraseñas y archivos. Para esto vamos a crear un certificado autofirmado válido por un año, con este comando en el cual ya le pasamos los datos con -subj: sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.key -out /etc/ssl/certs/vsftpd.crt -subj "/C=ES/ST=Andalusia/L=Huelva/O=Hosting/CN=192.168.197.152"

<img width="1055" height="280" alt="image" src="https://github.com/user-attachments/assets/355e8027-044c-443a-92fb-109f8ef30997" />

Ahora nos vamos al archivo de congifuración del vsftpd y descomentamos la linea write_enable para permitir que los usuarios puedan subir archivos mediante FTP:

<img width="754" height="455" alt="image" src="https://github.com/user-attachments/assets/49308ce1-c9fd-41b5-bc9f-e9d9c056567c" />

Y cambiamos las lineas finales para que apunte a nuestro certificado TLS:

<img width="525" height="184" alt="image" src="https://github.com/user-attachments/assets/934086c5-7e1d-40ad-8a94-f90cffa3573c" />

Ahora guardamos los cambios y reiniciamos el servicio. Para comprobar que el certificado esté aplicado correctamente, usamos este comando: openssl s_client -connect 127.0.0.1:21 -starttls ftp (este comando devuelve muchas lineas, por lo que no sale el inicio pero ha funcionado correctamente)

<img width="799" height="534" alt="image" src="https://github.com/user-attachments/assets/0d42b03f-6d95-4270-ac95-2e00738533bd" />

### 3.2 Preparar las zonas DNS
Nuestro script creará los subdominios, pero para que pueda hacerlo, primero debe existir el dominio principal. Vamos a llamarlo midominio.local y a declarar las zonas en bind poniéndolas en el archivo de configuración:

<img width="317" height="132" alt="image" src="https://github.com/user-attachments/assets/2c21f8e2-73f4-485e-80ce-103156de3962" />

Ahora creamos la zona directoa:

<img width="659" height="168" alt="image" src="https://github.com/user-attachments/assets/575a6310-6673-4a9e-9c93-82201b10d5fd" />

Y comprobamos:

<img width="588" height="65" alt="image" src="https://github.com/user-attachments/assets/cbc7efae-338a-4645-a872-38779a8e53de" />

Ahora creamos la zona inversa:

<img width="462" height="154" alt="image" src="https://github.com/user-attachments/assets/189ee9c8-7191-4025-9643-3190930c6857" />

Y comprobamos tambien:

<img width="590" height="55" alt="image" src="https://github.com/user-attachments/assets/b33b6099-b516-46e8-9588-b90306143b8f" />

Y reiniciamos el servicio:

<img width="593" height="179" alt="image" src="https://github.com/user-attachments/assets/aff38cf0-68f0-4d35-93da-5ad01d735d2b" />

Y combrobamos con dig:

<img width="426" height="31" alt="image" src="https://github.com/user-attachments/assets/d47289f2-fef6-49aa-9a5c-fea225a88b84" />

### 3.3 Habilitar python

Como ya instalamos el paquete libapache2-mod-wsgi-py3 en la fase anterior, solo tenemos que decirle a Apache que lo active. Usamos estos dos comandos:

<img width="370" height="85" alt="image" src="https://github.com/user-attachments/assets/cd040d8a-8109-460c-8884-f707a41cca01" />

Y comprobamos:

<img width="1075" height="134" alt="image" src="https://github.com/user-attachments/assets/cf7cc65d-1799-4a34-a3dc-852acfafa1da" />





