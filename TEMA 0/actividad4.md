**Busca información sobre el comando curl y muestra al menos cinco ejemplos de uso**

cURL es una herramienta de línea de comandos muy usada para transferir datos desde o hacia un servidor, usando los protocolos más comunes de Internet. Usa la librería libcurl  
Sintaxis: curl [OPCIONES] URL  
Permite hacer peticiones HTTP (GET, POST, PUT, DELETE…), subir archivos, autenticarse con usuario/contraseña, manejar cabeceras, seguir redireccionamientos, etc. También soporta muchas opciones para modificar el comportamiento.

**Algunos ejemplos**
curl https://www.ejemplo.com/: Realiza una petición GET al sitio y muestra el contenido HTML.  
curl -I https://www.ejemplo.com/: Obtiene solo las cabeceras HTTP.  
curl -o archivo.html https://www.ejemplo.com/pagina.html: Descarga la página y la guarda localmente con el nombre archivo.html.  
curl -O https://www.ejemplo.com/imagen.jpg: Descarga la imagen y la guarda con el nombre original. La opción -O toma el nombre del recurso remoto.  
curl -X POST -d "usuario=juan&clave=secreto" https://api.ejemplo.com/login: Envía datos (formato application/x-www-form-urlencoded) mediante POST a una API o formulario web. 
