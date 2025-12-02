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







