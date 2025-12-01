# Actividad 5

**1. Crea un directorio llamado "dir1" y otro llamado "dir2".**
<img width="926" height="69" alt="image" src="https://github.com/user-attachments/assets/682e7800-12a8-4dac-8a1c-1d1e7e36057b" />

**2. Explica qué diferencia existe entre ambos y muestra su equivalencia con la directiva Require:**
~~~~
<Directory /var/www/example1>
Order Deny,Allow
Deny from All
Allow from 192.168.1.100
</Directory>


<Directory /var/www/example1>
Order Allow,Deny
Deny from All
Allow from 192.168.1.100
</Directory>
~~~~
La diferencia está en el orden en el que Apache permite o deniega el acceso en este caso. En el primer caso, primero denegará todo el acceso de forma predeterminada y luego permitirá la conexión desde 192.168.1.100 y en el segundo ejemplo primero permitirá todo el acceso de forma predeterminada y luego denegará el acceso a todos excepto a 192.168.1.100 (whitelist y blacklist).

La sintaxis de la directiva require que haría lo mismo sería esta. Esta directiva solo nos permite la conexión desde esa ip en específico.
~~~~
<Directory /var/www/example1>
    Require ip 192.168.1.100
</Directory>
~~~~

**3. Para dir1**

A partir de aqui todo se hace en etc/apache2/apache2.conf:

a. Permite el acceso de las peticiones provenientes de 10.3.0.100  
<img width="292" height="70" alt="image" src="https://github.com/user-attachments/assets/8237f883-e985-4248-9808-98dadbf99993" />

b. Permite el acceso desde "marisma.intranet"  
<img width="374" height="68" alt="image" src="https://github.com/user-attachments/assets/47a9ec55-c948-4d37-bf58-b6edcc79dd71" />

c. Permite el acceso desde cualquier subdominio de "marisma.intranet"  
<img width="374" height="85" alt="image" src="https://github.com/user-attachments/assets/e83c4b53-129c-4c07-b287-096dfa18ceca" />

d. Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"  
<img width="301" height="71" alt="image" src="https://github.com/user-attachments/assets/7d345511-1289-456b-b0f5-baae61c20f66" />

**4. Modifica la configuración de forma que el acceso a dir1 se permita a "marisma.intranet" y no se permita desde 10.3.0.101"**

<img width="431" height="125" alt="image" src="https://github.com/user-attachments/assets/99cbdb17-8239-4523-8814-182ad51247b2" />

**5. Modifica la configuración de forma que el acceso a dir2 se permita a "10.3.0.100/8" y no a "marisma.intranet"**

<img width="476" height="116" alt="image" src="https://github.com/user-attachments/assets/c68fbe43-9f10-42b0-a7d6-b84311f4d523" />

