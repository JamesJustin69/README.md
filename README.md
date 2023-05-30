# Tarea 2: MySQL
> Esta tarea es acerca de montar un servidor MySQL con un cliente Dbeaver, utilizando DockerFiels
> Informe en LaTeX [Overleaf](https://www.overleaf.com/read/qcqzhzmrvbkx)

## Tabla de Contenidos
* [Información General](#información-general)
* [Tecnologías Utilizadas](#tecnologías-utilizadas)
* [Características](#características)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Uso](#uso)

## Información General
- Este proyecto consta de elaborar dos Dockerfiles, para servidor y cliente. La idea de usar Dockerfiles permite el uso automatizado de la creacion del servidor MySQL.
- El mayor obstáculo que se tuvo fue a la hora de crear el Dockerfile del servidor MySQL, en la parte de conexión, pero tuvo una rapida solucion a la hora de indagar un poco en el tema de Docker y el protocolo MySQL.
- FInalmente se pudo obtener un análisis correcto, gracias al buen manejo de Docker, esto usando Wireshark.

## Tecnologías Utilizadas
- Wireshark
- Docker
- MySQL
- Dbeaver


## Características
Algunas características que fueron implementadas:
- Dockerfiles, una función de Docker
- Análisis de tráfico con Wireshark
- Servidor MySQL, Bases de datos de prueba


## Screenshots

[Direccion de CloudBeaver](![extraccion de url](https://github.com/JamesJustin69/README.md/assets/89882424/0f75b6e8-54d3-4861-9d18-c99a02ba1cac)
[Cliente Dbeaver](![clientedbeaver](https://github.com/JamesJustin69/README.md/assets/89882424/d0f13b19-8448-4974-9a62-0d42f644cf3e)
[Setear cliente](![setear cliente](https://github.com/JamesJustin69/README.md/assets/89882424/0f237701-40f9-4edf-b933-dbfa5417de7e)
[vericación]![server configured](https://github.com/JamesJustin69/README.md/assets/89882424/ff12458f-2d24-4230-ab8f-405de9e2ddcc)
[SQL](![sql](https://github.com/JamesJustin69/README.md/assets/89882424/6974130e-f612-4b2d-9e24-e064408ec030)
[Análisis de trafico con Wiresharc](![trafico](https://github.com/JamesJustin69/README.md/assets/89882424/c59d2749-6d67-430e-a573-777ff5bbdc3e)
)

## Setup
Para empezar a desarrollar este proyecto, se necesitan algunas dependencias como Docker, Wireshark, también la descarga del protocolo seleccionado (el servidor y el cliente).

Posteriormente, hay que descargar imágenes en Docker, configurar Dockerfiles, esto para poder inicializar el servidor de forma automatizada, y el cliente.

Finalmente, una vez ya estando todo funcionando, se puede notar un tráfico de paquetes MySQL al momento de capturar con Wireshark.


## Uso
*Para poder completar la tarea (una vez instalado adecuadamente todo) lo primero sería crear un Dockerfile para el server y para el cliente, para el servidor   MySQL se deben poner las siguientes líneas de texto:
- FROM mysql:latest
- ENV MYSQL_ALLOW_EMPTY_PASSWORD="true"
- EXPOSE 3306
- CMD ["mysqld"]
*y las siguientes para el cliente Dbeaver:
- FROM dbeaver/cloudbeaver:latest
- ARG CLOUDBEAVER_VERSION=latest
- EXPOSE 8080
Con ambos dockerfiles listos, se ejecutan con los siguientes comandos:
-sudo docker run -p 3306:3306 -it mysql-server
-sudo docker run -ti --net=host dbeaver-client
Aca, se le indica al server que mapee el puerto interno del docker con el de la maquina, para asi poder acceder a el desde el cliente, y al cliente DBeaver se le indica que use la configuracion de red del host.

Iniciados los servicios, la consola de DBeaver uestra donde se encuentra la interfaz del cliente, accedemos a esta dirección y se procede a configurar el cliente con un usuario y contraseña, luego se utilizan estas credenciales para acceder y crear la colexión con el servidor MYSQL, como se indicó en el dockerfile el servidor, ENV MYSQL_ALLOW_EMPTY_PASSWORD="true", el usuario root notiene contraseña entonces el unico valor que necesitamos ingresar para la conexión es el nombre de usuario "root".
Ya stablecida la conexión se pueden generar consultas a la base de dato presente en el servidor.
