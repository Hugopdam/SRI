# Actividad 0 - Docker

## Fundamentos de Docker

Docker consiste en una herramienta *open-source* diseñada para facilitar y automatizar la distribución de software, encapsulando las aplicaciones en unidades ágiles y livianas conocidas como contenedores.

La meta fundamental de esta tecnología es erradicar el típico inconveniente de "funciona en mi ordenador, pero falla en producción". Al agrupar el programa junto con todo lo que necesita para operar (archivos de configuración, bibliotecas y demás dependencias), Docker asegura que el software tendrá un comportamiento idéntico sin importar el entorno o servidor donde se despliegue.

## Diferencia entre Imágenes y Contenedores

Suele haber confusión entre ambos términos, pero resulta muy fácil distinguirlos si hacemos la analogía entre una receta de cocina y el platillo finalizado:

* **Imagen de Docker:** Actúa como un molde o plantilla inmutable (de solo lectura). Guarda todos los elementos y directrices requeridos para dar vida a un contenedor. Una imagen no se ejecuta directamente, sino que sirve como base de construcción.
* **Contenedor de Docker:** Representa la versión activa y en funcionamiento creada a partir de una imagen. Siguiendo la metáfora anterior, si la imagen es la receta escrita, el contenedor sería el postre listo para comer. Estos tienen un ciclo de vida propio, por lo que pueden ser arrancados, pausados, trasladados o eliminados de manera independiente.

## Volúmenes y almacenamiento de datos

De forma predeterminada, la naturaleza de los contenedores es temporal (efímera): al eliminar un contenedor, toda la información almacenada en su interior se pierde de manera definitiva.

Para evitar esto y lograr que la información persista, Docker emplea los llamados "volúmenes". Estos funcionan como si fuesen discos duros externos virtuales que se vinculan al contenedor. Gracias a este mecanismo, los datos críticos (como los registros de una base de datos o los archivos de los usuarios) se mantienen protegidos en el equipo principal (máquina *host*), incluso si el contenedor original es destruido o reemplazado por una nueva actualización.
