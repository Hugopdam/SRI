# Proyecto 1º trimestre

Para hacer este proyecto tenemos una maquina ubuntu 25.10 limpia la cual vamos a actualizar mediante sudo pat update y upgrade.

## 1.- Dominios mediante el archivo hosts.

En total en esta práctica necesitamos 3 dominios aunque no los usemos todos al inicio, pero lo dejare hecho. para esto nos vamos a /etc/hosts y creamos los dominios:  
<img width="705" height="143" alt="image" src="https://github.com/user-attachments/assets/a2a5f3b9-f853-40a9-9392-53cff4527000" />

Para probarlo haremos pinmg a uno de ellos y veremos que funciona:  
<img width="658" height="123" alt="image" src="https://github.com/user-attachments/assets/d69277fe-ca65-40db-ab7e-ca6b66d0b1d3" />

## 2.- Instalación de la pila LAMP

Para instalar LAMP hacemos el siguiente comando:  
<img width="1157" height="160" alt="image" src="https://github.com/user-attachments/assets/b2e85c8b-769c-4911-8eb2-cb79dc0cd02e" />
e
Esto instala todo LAMP desde un solo comando y todas sus dependencias

Ahora vamos a iniciar el servicio y comprobamos su estado con los siguientes comandos:  
<img width="1025" height="179" alt="image" src="https://github.com/user-attachments/assets/b399b645-fccc-4c7e-9bc3-5e49dd60b174" />

## 3.- Instalación y Configuración de WordPress

"centro.intranet" será un wordpress, por lo que le crearemos una base de datos la cual es necesaria para que funcione WP. Lo vamos a hacer mediante mysql ya que tenemos LAMP:  
Una vez en mysql ponemos los siguientes comandos:

<img width="690" height="254" alt="image" src="https://github.com/user-attachments/assets/5fd94c4c-8dac-41c6-b6b2-ee6c6113485c" />

Ahora descargamos wp con el siguiente comando:  
<img width="1106" height="236" alt="image" src="https://github.com/user-attachments/assets/1510247a-3bfb-41b6-a2c0-53192f8d9e82" />

Y ahora decomprimimos y modificamos los permisos de la siguiente forma:  
<img width="552" height="67" alt="image" src="https://github.com/user-attachments/assets/423b8f01-e871-46a8-8cf3-94b6a3e92722" />  
<img width="812" height="76" alt="image" src="https://github.com/user-attachments/assets/40c24663-9e9d-482a-9586-40778ec84095" />  

Por ultimo creamos el fichero virtualhost:  
<img width="800" height="249" alt="image" src="https://github.com/user-attachments/assets/c2f1a58c-efd8-4787-bd6c-b4374abb9582" />

Ahora lo habilitamos:  
<img width="628" height="142" alt="image" src="https://github.com/user-attachments/assets/f585f4ed-80ea-4b4e-bd59-0ca9ff416995" />

Ahora para probarlo nos vamos a internet y ponemos http://centro.intranet:  
<img width="808" height="684" alt="image" src="https://github.com/user-attachments/assets/027005e6-1a94-4436-94e5-9c6fd7e3d57e" />

Terminamos la configuración:  
<img width="753" height="514" alt="image" src="https://github.com/user-attachments/assets/e1d164d3-d652-4b39-9d47-eaa00c9e8b6c" />

<img width="765" height="580" alt="image" src="https://github.com/user-attachments/assets/6ecee793-0fc6-409f-a04e-1adb8ac4141c" />

<img width="720" height="301" alt="image" src="https://github.com/user-attachments/assets/07263fd6-0c43-4b5e-878c-df290a2287d9" />

Y con esto ya estaria:  

<img width="1157" height="690" alt="image" src="https://github.com/user-attachments/assets/5f2ac30f-ceed-448b-81ce-96703ec6ef86" />

## 4.- Aplicación Python con WSGI

Primero lo instalamos con este comando:  
<img width="933" height="118" alt="image" src="https://github.com/user-attachments/assets/30f6361e-9c68-40eb-9e91-32947e3fef3b" />

Ahora creamos la carpeta donde ira el script (el script usado es uno creado en el momento muy sencillo simplemente para probar el funcionamiento):  

<img width="754" height="46" alt="image" src="https://github.com/user-attachments/assets/b17d4c6f-b750-4064-86ce-38c3322d3b93" />

Ahora creamos el virtualhost para python:  
<img width="848" height="261" alt="image" src="https://github.com/user-attachments/assets/01250ca0-3725-4f65-a76b-2b3e0021269a" />

Ahora lo habilitamos:  
<img width="641" height="107" alt="image" src="https://github.com/user-attachments/assets/5bf69006-f267-4258-9fe1-2ffbec569f7f" />

Ahora lo probamos:

<img width="617" height="101" alt="image" src="https://github.com/user-attachments/assets/e35d18cc-10fd-41c5-ba43-0d1c5690dd11" />

## 5.- Proteger Python con Autenticación

Primnero creamos el usuario y el archivo de contraseñas:  
<img width="794" height="94" alt="image" src="https://github.com/user-attachments/assets/3f96a8aa-a6a0-41f6-a798-b010120db412" />

Y ahora vamos a modificar el archivo de configuración del VirtualHost, dentro de directory vamos a añadir el método de autenticación y el require se cambiará por valid-user:  
<img width="555" height="287" alt="image" src="https://github.com/user-attachments/assets/1468d7f7-0818-43da-9ec0-1178deb3d80b" />

Y si ahora recargamos apache y probamos a entrar a departamentos otra vezs nos pedirá el login:  
<img width="711" height="344" alt="image" src="https://github.com/user-attachments/assets/dca46439-5393-4f9f-b9d7-f38e0abc0c7f" />

## 6.- Instalar y Configurar AWStats

Instalamos awstats con el siguiente comando:  
<img width="915" height="124" alt="image" src="https://github.com/user-attachments/assets/1d69d674-2809-4514-a592-72163b0da474" />

Vamos a configurarla para centro.intranet, copiando la configuración base:  
<img width="1081" height="58" alt="image" src="https://github.com/user-attachments/assets/a236af3a-7520-4592-b4ea-a3a48bda1b99" />

Y modificamos estas lineas para que corresponda con nuestro trabajo:  
<img width="461" height="37" alt="image" src="https://github.com/user-attachments/assets/1890d926-7dea-4c79-95a6-41e01b2428e3" />
<img width="273" height="28" alt="image" src="https://github.com/user-attachments/assets/bf92e4cd-952a-4094-9b60-43ba120fdf3b" />

Ahora vamos a habilitar CGI para poder ver las gráficas. Reiniciaremos apache tambien:  
<img width="631" height="150" alt="image" src="https://github.com/user-attachments/assets/4a521c5a-6cc7-4738-9111-50fb0d91f2fd" />

Como último paso, generamos las estadísticas iniciales con:  
<img width="1132" height="298" alt="image" src="https://github.com/user-attachments/assets/086e6731-50b8-47a9-a724-7b2159ad22d8" />

Y ahora comprobamos:  
<img width="1152" height="457" alt="image" src="https://github.com/user-attachments/assets/554788fd-de66-4617-8cdf-368f0ae992b8" />

## 7.- NGINX y PHPMyAdmin

Para que no haya interferencias entre apache y nginx, nginx y phpmyadmin lo vamos a poner en el puerto 8080. Primero, lo instalamos. Como Apache usa PHP como módulo, Nginx necesita php-fpm, así que instalamos ambos:  
<img width="620" height="20" alt="image" src="https://github.com/user-attachments/assets/8067eaca-fdda-45ec-b18e-a7b78c398b55" />

Si nos da error (que es casi seguro) es porque nginex usa el purto 80 que ya esta ocupado por apache, asi que ahremos lo siguiente. Nos vamos a este archivo:  
<img width="775" height="29" alt="image" src="https://github.com/user-attachments/assets/49af02c2-1c85-42c0-a9a1-64ca9d8bf564" />

Y modificaremos las siguientes cosas:  
<img width="395" height="84" alt="image" src="https://github.com/user-attachments/assets/806c824e-eae3-4b71-9ea0-bef0c692554d" />
<img width="634" height="70" alt="image" src="https://github.com/user-attachments/assets/5d6be0d6-b331-4d7e-8dc1-2b2994c4cd66" />
<img width="540" height="176" alt="image" src="https://github.com/user-attachments/assets/3b534cf8-9537-47ab-93b4-af6a48eacd37" />

Y ahora reiniciamos el servicio y veremos que funciona:  
<img width="1151" height="409" alt="image" src="https://github.com/user-attachments/assets/f4245048-9fbe-4221-ae78-f3964b1eb939" />

Lo siguiente va a ser instalar PHPMyAdmin:  
<img width="919" height="170" alt="image" src="https://github.com/user-attachments/assets/e485a0b4-2937-422b-9087-1951b70dfb55" />

Nos llevara a la configuración de phpmyadmin. En la primera no marcamos nada y aceptamos:  
<img width="1065" height="291" alt="image" src="https://github.com/user-attachments/assets/038fea0f-6d0d-4f01-8ae1-43b0eb04386e" />
<img width="1139" height="373" alt="image" src="https://github.com/user-attachments/assets/209269be-521e-4fe1-ab4a-4a99ca3480bb" />
<img width="1129" height="260" alt="image" src="https://github.com/user-attachments/assets/cdfdd1c4-9a2c-4284-828a-0b849f1136c4" />

Ahora ponemos este comando para vincular nginx:  
<img width="724" height="22" alt="image" src="https://github.com/user-attachments/assets/2d6fd408-0962-4cca-a3c2-f7e5866468ed" />

Y ahora nos vamos a internet y ponemos la url http://servidor2.centro.intranet:8080/phpmyadmin y veremos que funciona:  
<img width="778" height="520" alt="image" src="https://github.com/user-attachments/assets/cee3c4e2-69ac-4bc7-b655-3e058bdda022" />








