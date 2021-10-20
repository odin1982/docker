# docker
    Es una herramienta que despliega aplicaciones en contenedores de forma rapida y portable.

## Arquitectura Docker
    Docker Host (Servidor donde se aloja docker)

    Contenedor      Imagenes    Volumenes   Redes
                Docker CLI - Client
                    Rest API
                Cocker Daemon -Server

## Que es una imagen
    Un paquete que contiene toda la configuracion para que funcione o se pueda ejecutar el servicio.



                    Capa3 - CMD(Lo que va a levantar el servicio)
                    Capa2 - RUN
                    Capa1 - FROM(Que Sistema Operativo vamos a tener)

Capa1,Capa2,Capa3 son de solo lectura

DockerFile se definen las capas que queramos.

## Que es un contenedor
    Una capa adicional que trae una ejecucion en tiempo real de las capas anteriores

    Contiene Imagenes, Volúmenes, Redes,

## Contenedores vs Maquinas Virtuales

    Contenedor: Una instancia en ejecucion de una imagen

## Creando nuestra primer imagen
    1.- Crear carpeta [nombre-carpeta]
    2.- Crear Dockerfile.txt
    3.- Agregar al archivo

            FROM centos
            RUN yum install httpd -y

        NOTA: Se esta agregando Centos y Apache
    4.-  Crear imagen
        $ docker build --tag apache-centos .# docker


## Dockerfile
    Archivo de configuracion de la imagen
    FROM    --> especificamos que S.O o una imagen misma
    RUN     --> Instrucciones que se ejecutan en la terminal
    COPY/ADD    --> Copiar archivos desde nuestra computadora a la imagen
    ENV     --> Variables de entorno
    WORKDIR --> Directorios de trabajo
    EXPOSE  --> Exponer puertos, modifica el puerto al que quieres desplegar tu aplicación 
    LABEL   --> Etiquetas, sirven comunmente metadata de la imagen
    USER    --> Que usuario ejecutara la tarea
    VOLUME  --> Volumenes
    CMD     --> Lo que va a levantar el servicio
    .dockerignore


La diferencia entre COPY y ADD es que ADD permite copiar URL's


## Buenas practicas Dockerfile
    Imagen Efimera-que se puede destruir con gran facilidad
    Un servicio por contenedor
    Pocas capas
    Separar argumentos largos en diferentes lineas
    Varios argumentos en una sola capa
    No instalar paquetes inecesarios
    Labels

## Dangling images
    Son imagenes con el mismo nombre pero su contenido de la capa es distinto como las capas son de solo lectura docker crea una imagen nueva y crea una nueva referencia

    apache                 ssl       347ee054c54d   18 hours ago   401MB
    <none>                 <none>    b38b614833ec   18 hours ago   401MB        *** Dagling images


## CONTENEDORES
    Son una instancia de ejecución  de una imagen
    Son temporales
    Capa de RW( read - write )
    Crear varios contenedores de una misma imagen

    Se puede tener varios contenedores corriendo por varios puertos con la misma imagen
    docker run -d -p 8090:8080 jenkins/jenkins

## VARIABLES DE ENTORNO
    Pueden existir en dos lugares:
        * Dockerfile

## CREAR CONTENEDOR MONGO
    * buscar imagen dokcker mongo
    * https://hub.docker.com/_/mongo
    * $ docker pull mongo
    * $ docker run -d --name [nombre-contenedor] -p [puerto-mapear]:[puerto-default-mongo] [nombre-imagen]
      $ docker run -d --name my-mongo2 -p 27018:27017 mongo
    * como saber cuanta memoria esta usando mi contenedor
        $ docker stats [nombre-contenedor]