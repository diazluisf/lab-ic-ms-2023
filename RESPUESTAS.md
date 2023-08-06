# Respuestas

Indica tu nombre a continuación: 

Por cada etapa agrega una sección abajo y escribe las respuestas a las preguntas de cada etapa.

## ETAPA 1

La diferencia entre los archivos que contienen el verbo `Create` con los archivos que contienen el verbo `Add`
es que el `Create` indica instrucciones de creación de nuevas tablas, mientras que el `Add` realiza inserciones
a las tablas creadas.

El servicio que se declara es flyway

El comando que se pasa a Flyway dentro del contenedor es "-locations=filesystem:/flyway/sql -connectRetries=60 migrate". Esto le indica a Flyway que busque las migraciones en el directorio "flyway/sql" dentro del contenedor y que intente conectarse a la base de datos PostgreSQL y aplique las migraciones.

## ETAPA 2

Al modificar el nombre del servicio de postgres a db se tiene un error porque el servicio definido como `flyway`
se indica que tiene una dependencia sobre el servicio de nombre `postgres` por lo que también se debe modificar esa dependencia a `db`.

## ETAPA 3
¿Qué te llama la atención?
En principio, el hecho de que el archivo dockerfile esta utilizando un enfoque de construccion en múltiples etapas, separando el entorno de compilación del entorno de producción final.
Tambien es interesante que se escoja hacer un cambio de usuario, asumiría que es debido a motivos de seguridad.

El dockerfile de movies-api se encarga de construir la aplicación a partir del código fuente de GO, el cual posteriormente es utilizado en la configuración del servicio movies-api dentro del docker-compose.yaml.

El atributo `context` debe estar especificando el directorio para la construcción de la imagen del servicio movies-api. Ese contexto actua como la ruta del directorio local que contiene el Dockerfile y los archivos que se ocupen para construir la imagen.

#### Opcional:
    Al modificar la variable BIND_IP a `localhost` no se tiene respuesta al intentar consultar la api. Esto es debido a que se estaría configurando el servicio para escuchar solo en localhost, limitando el acceso desde fuera de la máquina en la que se encuentra el contenedor.

## ETAPA 4
La diferencia entre los atributos build del servicio movies-api y movies-front es que el servicio movies-api utiliza la opción context para especificar la ruta del directorio de compilación, mientras que el servicio movies-front solo especifica el nombre del directorio de compilación directamente. La opción context en el servicio movies-api permite especificar una ruta relativa al archivo docker-compose.yaml para el directorio de compilación.

Si los atributos build para movies-api y movies-front se dejan iguales, no hay ninguna diferencia real en cuanto al funcionamiento de los servicios. Ambos aún utilizán el directorio especificado en ./movies-api y ./movies-front respectivamente para la compilación de las imágenes del contenedor