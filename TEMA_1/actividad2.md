# Configuración Apache:

**Añadir el puerto 81**

Añadimos la línea 'Listen 81' al archivo ports.conf:
<img width="728" height="140" alt="image" src="https://github.com/user-attachments/assets/f64a6857-7907-437f-a62c-23d0d56096cc" />

Reiniciamos apache y ya estaría:
<img width="1098" height="541" alt="image" src="https://github.com/user-attachments/assets/72b5e57c-6a54-4e97-9963-d427dd276ffa" />

**Añadir el dominio “marisma.intranet” en el fichero hosts**
<img width="742" height="107" alt="image" src="https://github.com/user-attachments/assets/2f544cd3-7f97-4966-ba40-76eb08a51d4f" />

Ahora reiniciamos apache otra vez y ya estría:  
<img width="593" height="237" alt="image" src="https://github.com/user-attachments/assets/f4d1427a-8773-456e-a698-6a0b9aba5ee0" />

**Cambiar la directiva “ServerTokens” para mostrar el nombre del producto.**
En el arvhido security.conf ponemos servertokens prod:
<img width="897" height="516" alt="image" src="https://github.com/user-attachments/assets/514ea141-a2d0-4c07-818e-b823a71e1823" />

Y así logramos que solo nos muestre el nombre del producto y no la versión ni el OS (tendremos que recargar apache primero):
<img width="980" height="175" alt="image" src="https://github.com/user-attachments/assets/258da762-4d78-42b3-891b-2a880ff4985d" />

**Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva "ServerSignature" y comprueba que funciona correctamente.**
Comprobamos que primerop sale
<img width="516" height="193" alt="image" src="https://github.com/user-attachments/assets/0007d92c-56e8-444c-ba39-2ffeeb9d0c16" />

 Modificando en el mismo fichero que antes un poco mas abajo el parametro serversignature y poniendolo en off veremos que desaparece:
 <img width="479" height="166" alt="image" src="https://github.com/user-attachments/assets/376ebddf-8d47-493f-8bdb-04fc2d3a6ab5" />

 **Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas**
 <img width="915" height="55" alt="image" src="https://github.com/user-attachments/assets/c50df22e-5382-42ff-8e6e-e6ddd6b1c049" />

Este es prueba 1:
<img width="951" height="333" alt="image" src="https://github.com/user-attachments/assets/51c783fc-91ac-436d-91ef-8a5c4b66b289" />

Esta es prueba 2:
<img width="979" height="353" alt="image" src="https://github.com/user-attachments/assets/aad89795-8e7c-477d-8d5a-d7889a5a6678" />

**Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”**

Dentro de /etc/apache2/ vamos al archivo apache2.conf y añadimos la línea siguiente:  
<img width="266" height="25" alt="image" src="https://github.com/user-attachments/assets/ff4261e6-5234-48ee-8a6f-6469c686ba6e" />  
Ahora si reiniciamos apache y escribimos localhost/pureba1 nos llevara instantaneamente a preuba2

Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.
Si es posible. Tenemos que escribir esta codigo:  
<img width="389" height="60" alt="image" src="https://github.com/user-attachments/assets/5007cf54-1133-4578-8591-6985b9cdc4ce" />

Ahora si nos fueramos a prueba 1 nos llevaria concretamente al fichero especificado. Si tuvieramos otro fichero con ese nombre se nos mostraría.  
<img width="586" height="158" alt="image" src="https://github.com/user-attachments/assets/65b4fd6f-da77-42fb-9634-275d8a7e7ded" />

**Usa la directiva userdir**
