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
