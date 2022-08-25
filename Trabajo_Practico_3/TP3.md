¿Cuales puertos estan abiertos?
- Los puertos levantados son el 5000 para la aplicación web y el 6379 para la db no esta abierto pero reservado.
¿Que comandos uso?
- docker ps: para ver los puertos levantados.
- docker network inspect {network_name}.

2) El sistema instancia un framework llamado Flask, luego se instancia el motor de DB Redis bajo el host de Redis.
se crea la variable **port** el cual es el puerto que esta reservado para Redis. **bind_port** es el puerto en el cual esta
escuchando la aplicación web. Luego se indica la ruta para correr la apliación. Se define una función **hello**, el cual utiliza el
motor de db para incrementar en 1 el atributo hits, se trae el dato de hits desde la DB y se imprime el texto con la variable **total_hits**.
Por ultimo se crea el main donde se corre el framework bajo el host 0.0.0.0 y el puerto 5000.

- Se utliza el **-e** para poder vincular un contenedor a otro usando el puerto del segundo y su nombre de host.
- Si se ejecuta **docker rm -f web** se elimina el contenedor de la aplicacion web y lo volvemos a correr nos va a mostrar los mismos datos
debido a que la informacion esta almacenada en el otro contenedor.
- Cuando borramos el contenedor de la DB, estamos eliminando toda la informacion que veniamos almacenando y si lo
corremos de vuelta empezamos con la informacion original.
3) El **docker compose** lo que hace es crear una red con distintos contenedores a partir de un archivo yaml, éste ademas de crear los contenedores y vincularlos
tambien los levanta y quedan corriendo hasta que se bajen con el **docker compose down**.
4) El sistema se levanta utilizando 2 networks ( **back-tier** y **front-tier**), se levantan 5 contenedores ( redis, postgres y 3 aplicaciones web, uno para votar,
otro para el resultado y un tercero llamado worker). 
Tanto la app web de voto y resultado escuchan en diferentes puertos (5000 y 5001 relativamente), el motor de DB escucha sobre el puerto 49513 y la base de datos
postgres tiene reservado el puerto 5432.
Se utiliza un solo volumen para por almacenar localmente los datos de la DB.

