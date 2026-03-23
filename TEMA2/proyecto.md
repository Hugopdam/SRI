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

Ya lo dejamos instalarse y cuando acabe, actualizaremos los repositorios para hacer la snapshot:
