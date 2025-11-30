# Actividad 0.1- HTTP Introduction

**¿Quién, dónde y cuándo se crea el primer servidor web?**

El primer servidor web fue creado por Tim Berners Lee en el CERn, en 1990.

**¿Qué pila de protocolos usa http?**
	
La pila de protocolos de HTTP, permite la comunicación en red. Digamos que es el “camino” que debe recorrer una petición HTTP pasando por las capas del modelo TCP/IP. 

**Componentes URL**

1. Protocolo: ejemplo http, https (protocolo que usará)  
2. Host/dominio: "www.ejemplo.com"  
3. Puerto (opcional, si no es el estándar): por ejemplo :80, :443  
4. Ruta: ubicación del recurso en el servidor  
5. Consulta (opcional): parte después de "?" para parámetros adicionales  
6. Fragmento (opcional): después de #, para referirse a una sección dentro del recurso  

**¿Pasos en la recuperación de una página web mediante HTTP?**

1. Usuario o navegador introduce una URL / hace clic en enlace.  
2. Se resuelve el nombre de dominio: Se pregunta qué dirección IP corresponde al dominio.  
3. Se establece conexión TCP al servidor web en el pierto correspondiente.  
4. Se envía la petición HTTP al servidor.  
5. El servidor procesa la petición: verifica el recurso. Puede implicar lectura de archivos estáticos o ejecutar código en caso de que fuera dinámico.  
6. Se crea la respuesta HTTP: línea de estado, encabezados (headers), tipo de contenido, longitud, etc., y finalmente el cuerpo (body) con el recurso (HTML, imagen, etc.).  
7. La respuesta vuelve al cliente por la conexión TCP.  
8. El navegador interpreta la respuesta: si es HTMLlo muetra. Si incluye CSS, JS, imágenes... hace peticiones adicionales.  
9. Cuando acaba, o se cierra la conexión TCP o se mantiene abierta si se usa HTTP persistente.  

**Diferencia entre páginas dinámicas y estáticas**
	
Páginas estáticas: el contenido que el servidor entrega es siempre el mismo para esa URL. No cambia según el usuario, o si cambia, el webmaster lo edita.  
Páginas dinámicas: el contenido se genera bajo demanda cuando llega la petición. Puede depender de datos en una base de datos, de la sesión del usuario, de parámetros, etc. Por ejemplo, un foro, un blog con comentarios, una tienda online.  

**Metodos request**

GET: solicita un recurso.
HEAD: como GET pero sólo obtiene los encabezados, no el resto del recurso.  
POST: enviar datos al servidor, puede producir cambios.  
PUT: reemplaza completamente un recurso existente o lo crea si no existe.  
DELETE: eliminar un recurso.  
También existen: OPTIONS, PATCH, TRACE, CONNECT dependiendo del uso.  

**Codigos respones**

1xx: La petición se recibió, pero el servidor sigue procesando  
2xx: La petición fue satisfactoria
3xx: El cliente debe hacer algo adicional para completar la petición.  
4xx: La petición fue mala o no tiene permisos.  
5xx: La petición es correcta, pero el servidor falló  

**Content Type**

Es un encabezado de la respuesta HTTP que indica qué tipo de contenido se está enviando:  
text/html: páginas HTML  
text/plain: texto plano  
text/css: hojas de estilo CSS  
application/javascript o text/javascript: scripts JS  
application/json: datos en formato JSON  
image/jpeg, image/png, image/gif: imágenes  
application/xml: XML (aunque cada vez menos usado excepto APIs antiguas)  
