# Subdominios
El ejercicio pide crear iesmarisma.intranet, pero como ya tenemos funcionando marisma.intranet de la práctica anterior, lo que voy a hacer es crear el subdominio informatica.marisma.intranet. Voy usar el método de Subdominio Virtual, que es  lo más fácil y menos propenso a errores.

Para esto, lo que tengo que hacer es editar el fichero de zona de marisma.intranet. Aquí nos aseguraremos de tener los hosts principales (smtp, ftp. www) y crearemos los del subdominio:

<img width="473" height="356" alt="image" src="https://github.com/user-attachments/assets/2def3c65-5953-4c55-888e-2524598fd604" />

Comprobamos la sintaxis y si da OK reiniciamos el servicio:

<img width="731" height="62" alt="image" src="https://github.com/user-attachments/assets/850c8c50-dea5-46b5-ba11-50a7faf9e789" />

Ahora nos vamos al cliente y vamos a comprobar las modificaciones hechas:

<img width="567" height="148" alt="image" src="https://github.com/user-attachments/assets/000e9957-f3e3-4928-89d9-7cb5704a52dc" />

<img width="537" height="343" alt="image" src="https://github.com/user-attachments/assets/08814c6f-69e9-4230-9c3d-897ef1a1ee9f" />

<img width="499" height="130" alt="image" src="https://github.com/user-attachments/assets/00d550eb-80aa-4361-94e1-709939bd39ac" />

## Scripts para crear subdominios.

### La directiva $INCLUDE

La instrucción $INCLUDE sirve para fragmentar la configuración de DNS, separando la zona principal de sus subdominios en archivos distintos. Usando nuestro escenario como ejemplo, mantendríamos el archivo base "marisma.intranet" y crearíamos uno nuevo exclusivo para "informatica.marisma.intranet". La clave está en añadir la directiva $INCLUDE dentro del archivo principal; de esta forma, BIND9 leerá e integrará automáticamente el contenido del archivo del subdominio, procesándolo como si estuviera escrito todo junto en un único documento.

### Script de bash

~~~
#!/bin/bash

# Pide subdominio e ip al usuario por teclado
read -p "Introduce el nombre del subdominio (ej: ventas): " SUBDOMINIO
read -p "Introduce la IP para este subdominio: " IP

ARCHIVO_MAIN="/etc/bind/db.marisma.intranet"
ARCHIVO_SUB="/etc/bind/db.$SUBDOMINIO"

# Crea el archivo .db con lo básico, los 3 hosts y lo guarda en el fichero del subdominio
echo "; Configuración para $SUBDOMINIO" | sudo tee $ARCHIVO_SUB
echo "www.$SUBDOMINIO   IN   A   $IP" | sudo tee -a $ARCHIVO_SUB
echo "ftp.$SUBDOMINIO   IN   A   $IP" | sudo tee -a $ARCHIVO_SUB
echo "smtp.$SUBDOMINIO  IN   A   $IP" | sudo tee -a $ARCHIVO_SUB

# Añade el INCLUDE al archivo principal comprobando si ya existe
if grep -q "$ARCHIVO_SUB" "$ARCHIVO_MAIN"; then
    echo "El subdominio ya estaba incluido en el archivo principal."
else
    echo "\$INCLUDE $ARCHIVO_SUB" | sudo tee -a $ARCHIVO_MAIN
    echo "Incluido nuevo archivo en la zona principal."
fi

# Reinicia BIND y comprueba
echo "Reiniciando BIND9..."
sudo systemctl restart named
sudo systemctl status named --no-pager
~~~

Y probamos el script:

<img width="750" height="474" alt="image" src="https://github.com/user-attachments/assets/8169827b-b809-4bfd-bed5-f8b9ff0d88ba" />

<img width="387" height="95" alt="image" src="https://github.com/user-attachments/assets/1cfda8ff-6f4f-45e3-8d8f-5aaba25b6bcb" />

<img width="524" height="124" alt="image" src="https://github.com/user-attachments/assets/da6fbca6-0015-4d98-bb5e-95eccfabf194" />
