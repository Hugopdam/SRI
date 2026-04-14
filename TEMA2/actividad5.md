# Actividad 5

Para esta practica lo primero que haremos será actualizar los repositorios de un ubuntu e instalarle Bind9:

<img width="800" height="240" alt="image" src="https://github.com/user-attachments/assets/1e263435-69e6-40a3-b40a-dafafe22763b" />

## Caching & Forwarding

Para configurarlo primero como un servidor de caché de DNS, nos vamos a /etc/bind y modificamos el named.conf.options:

<img width="451" height="155" alt="image" src="https://github.com/user-attachments/assets/1a1a075d-64c3-46f1-ae06-8d8681989f77" />

Aquí lo que vamos a declarar es una lista de control de entrada con el rango de IP que vamos a permitir que escuchen las peticiones que hagamos a nuestro servidor DNS. Vamos a añadir este bloque de ACL arriba del bloque options y a especificar los clientes en los que confiamos:

<img width="222" height="119" alt="image" src="https://github.com/user-attachments/assets/6ff82a11-fc22-4b2e-82e8-2c8542bf42ee" />

Ahora que ya tenemos estos clientes definidos, dentro de options vamos a permitir las consultas:

<img width="295" height="225" alt="image" src="https://github.com/user-attachments/assets/1e5406d0-1373-478b-a8e0-d3a7d976efec" />

Guardamos, y vamos a comprobar la sintaxis de nuestro archivo de configuración con sudo named-checkconf:

<img width="534" height="56" alt="image" src="https://github.com/user-attachments/assets/1dc11503-d595-420b-a765-a0750f44592f" />

Y reiniciamos bind para aplicar los cambios con sudo systemctl restart bind9. En los logs vemos que está escuchando la IP de nuestro servidor:

<img width="522" height="32" alt="image" src="https://github.com/user-attachments/assets/a8a4597d-972f-4810-b981-3f3963f3d972" />

## Forwarding

Ahora vamos a configurarlo además como un servidor forwarding. Para esto, en el mismo archivo que hemos modificado, simplemente descomentamos el bloque de forwarders y añadimos otras opciones. (Es la parte de arriba de la captura de options, solo que ahora lo descomentamos):

<img width="286" height="282" alt="image" src="https://github.com/user-attachments/assets/b12500ee-182f-4489-bee2-3caabb09bc35" />

## Comprobaciones

Después de configurar el archivo /etc/resolve.conf de la siguiente manera:

<img width="201" height="61" alt="image" src="https://github.com/user-attachments/assets/7da0b36d-2317-49bf-91e3-7f07c2068e92" />

Y ya con eso empezamos a probar con el cliente:

<img width="536" height="175" alt="image" src="https://github.com/user-attachments/assets/66af929f-83f0-41aa-a7a0-b4450e6ad5af" />

<img width="486" height="615" alt="image" src="https://github.com/user-attachments/assets/4989c5d1-45a6-437b-9d8d-143970a08eba" />



