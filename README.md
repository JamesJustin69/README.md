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
![Example screenshot](./img/screenshot.png)
<!-- If you have screenshots you'd like to share, include them here. -->
![Direccion de CloudBeaver](./

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

