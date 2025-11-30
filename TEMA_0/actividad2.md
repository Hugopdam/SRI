**Diferencias entre udp y tcp**

TCP (Transmission Control Protocol) y UDP (User Datagram Protocol) son dos protocolos de la capa de transporte, pero tienen diferencias claras.
TCP es un protocolo orientado a la conexión,por lo que establece una conexión segura entre el emisor y el receptor antes de comenzar la transmisión de datos.
Garantiza que los datos lleguen completos y en orden lo cual lo hace más seguro, aunque más lento debido al control de errores y a los mecanismos de verificación.
UDP es un protocolo que no esta orientado a la conexión. Es más rápido pero menos confiable, ya que no garantiza la entrega ni el orden de los paquetes.

**Aplicaciones que usan TCP**

Aplicaciones como HTTP (protocolo de transferencia de hipertexto), SMTP, POP e IMAP (protocolos para correos electrónicos), y SSH (protocolo seguro de acceso remoto).

**Aplicaciones que usan UDP**

Aplicaciones que priorizan la velocidad y toleran cierta pérdida de datos, como las directos en plataformas de streaming, videojuegos, DNS y VoIP.

**Donde se almacena el puerto**

En la capa de transporte.

**Donde  se almacena la direccion IP**

En la capa de red.

**Three-way handshake**

Three-way handshake es un proceso de tres pasos utilizado por TCP para establecer una conexión entre dos dispositivos.
Primero, el cliente envía un segmento SYN (synchronize) al servidor. Luego, el servidor responde con un segmento SYN-ACK (synchronize-acknowledge).
Finalmente, el cliente envía un ACK (acknowledge) al servidor, completando así el establecimiento de la conexión.
Este mecanismo garantiza que ambas partes estén listas para la transmisión de datos y sincronizadas correctamente.
