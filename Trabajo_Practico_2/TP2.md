4 - Al correr **docker run busybox**, no se obtiene ningun resultado porque se deberia instanciar un contenedor de esa imagen, una
imagen es solamente un directorio con todo el programa.
5 - Cuando se ejecuta **docker ps -a**, nos devuelve los diferentes contenedores creados, devolviendo el ID del contenedor, la imagen que
se uso, el status muestra si esta levantado o no el contenedor, los puertos que utiliza y el nombre del contenedor (puede ser auto-generado
o se le puede dar uno).
9 - Con **docker run** se levanta un contenedor, de manera que hasta que no se ejecute el comando de pararlo va a seguir levantado.
Con **docker exec** solamente se esta levantando ese contenedor durante su uso, si salimos del contenedor se para en el instante.
