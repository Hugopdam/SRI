La imagen de hellow-world:

<img width="704" height="560" alt="image" src="https://github.com/user-attachments/assets/75bd4426-c881-42b3-aaa7-2a25dcefa9a2" />

Vemos que al terminar de ejecutarse el proceso, se paran:

<img width="1008" height="84" alt="image" src="https://github.com/user-attachments/assets/833a9137-2997-44d8-bd48-e0e1631b115b" />

Podemos eliminar el contenedor con su nombre o id:

<img width="674" height="100" alt="image" src="https://github.com/user-attachments/assets/1a5b845f-b26e-497c-978e-9d4c5b9aad5a" />

Con docker run ejecutamos contenedores, y con docker images vemos las imágenes que tenemos descargadas:

<img width="1251" height="105" alt="image" src="https://github.com/user-attachments/assets/f5ac805b-9a6f-44c1-8ab3-0c4247632a6d" />

## Ejecutando un contenedor interactivo

Usamos -it para que sea interactiva y nos abra una terminal:

<img width="811" height="172" alt="image" src="https://github.com/user-attachments/assets/7d60dafa-86b2-49de-b116-bcd2baef7fdf" />

Si salimos se para pero nos podemos volver a conectar:

<img width="639" height="104" alt="image" src="https://github.com/user-attachments/assets/9f23d82e-cc84-4a0e-aeeb-1af2a7a9b444" />

Con exec ejecutamos comandos dentro del contenedor:

<img width="1032" height="512" alt="image" src="https://github.com/user-attachments/assets/7424b2ec-ca58-402e-b089-ae9ccb1142b9" />

Y con inspect nos da su información:

<img width="1253" height="495" alt="image" src="https://github.com/user-attachments/assets/5cd90ea8-d266-4c19-8442-c852b61f1a9d" />

## Creando un contenedor demonio

La opción -d del comando run hace que se ejecute en segundo plano, y bash -c nos permite ejecutar uno o mas comandos en el contenedor de forma más compleja.

<img width="1217" height="373" alt="image" src="https://github.com/user-attachments/assets/4d3a6f11-3660-425f-ba1e-14031e64a140" />

Vemos que se está ejecutando en segundo plano y lo que está haciendo. Por último lo borramos a la fuerza:

<img width="764" height="162" alt="image" src="https://github.com/user-attachments/assets/480945fa-28b9-428c-b1f4-3ad98e5e5ec6" />

## Creando un contenedor con un servidor web

Lo hacemos con la imagen de apache en dockerhub:

<img width="877" height="278" alt="image" src="https://github.com/user-attachments/assets/708abe8e-0d76-4c85-899c-d74250fa1165" />

Lo comprobamos accediendo a la IP del servidor con docker:

<img width="800" height="218" alt="image" src="https://github.com/user-attachments/assets/f17ec0bc-d718-492d-b8fb-70a66333a57b" />

Para modificarlo accedemos al contenedor con exec y creamos un index.html:

<img width="785" height="159" alt="image" src="https://github.com/user-attachments/assets/269e8e08-5672-403b-ad3c-8c520dbffcf2" />

## Configuración de contenedores con variables de entorno

Se hace con el flag -e o --env. Vamos a probarlo con MariaDB:

<img width="1195" height="410" alt="image" src="https://github.com/user-attachments/assets/876b622d-0fa1-41f3-b2c9-631ad2c6d505" />

<img width="703" height="191" alt="image" src="https://github.com/user-attachments/assets/943505dd-1042-43b1-9e34-a2c434a944f4" />
