---
layout: post
title: RUN/DOCKER/RUN&#58 Taller de introducción a Docker
date: 2017-03-24 18:51:00 -0300
author: vkmc
categories: eventos talleres
---

{% assign gallery_url = site.url | append: site.baseurl | append: "/assets/img/blog/photos/2017-03-24-taller-de-docker" %}

¿Escuchaste hablar sobre _containers_? Muy probablemente,
si la respuesta es sí, entonces seguramente te hablaron de Docker.
Siendo que es una tecnología que está teniendo tanta adopción
actualmente, decidimos hacer un taller introductorio y vamos a darlo
por primera vez en el marco del evento chicas.geek organizado por [IBM Argentina](https://twitter.com/EmpleosIBMLatam).

![chicas.geek IBM]({{gallery_url}}/chicas-geek-ibm.jpg)

<!--more-->

Para optimizar el tiempo del cual vamos a disponer, sea que vengas a
dicho evento o que veas esto más adelante y estemos dando nuevamente
el taller (¡cosa que realmente esperamos!) dejamos como requisito que vengas
con tu Mac/PC con Docker instalado. ¿Cómo lo instalás? Excelente pregunta.


# 1. Instalando Docker

Vamos a ver las instrucciones según el sistema operativo que uses.

## Docker en Mac

Docker en Mac es algo bastante nuevo. Corre una aplicación nativa de Mac y usa xhyve para
virtualizar el entorno de Docker Engine y las características específicas del kernel de
Linux para el daemon de Docker.

[Descargá Docker para Mac](https://download.docker.com/mac/stable/Docker.dmg)


### Requerimientos

- La Mac tiene que ser modelo 2010 o más nueva
- macOS 10.10.3 Yosemite o más nueva
- Por lo menos 4GB de RAM
- Una versión de VirtualBox mayor a 4.3.30 (¡IMPORTANTE! Para esta versión
y las anteriores, Docker fallará en la instalación)

**Si tenés una versión de mac anterior a 2010 seguí las instrucciones de [Docker para versiones viejas](#docker-para-versiones-viejas)**



## Docker en Windows

Docker en Windows es algo bastante nuevo también. Corre una aplicación nativa de Windows y
usa Hyper-V para virtualizar el entorno de Docker Engine y las características específicas
del kernel de Linux para el daemon de Docker.

[Descargá Docker para Windows](https://download.docker.com/win/stable/InstallDocker.msi)


### Requerimientos

- *Windows 10 64bit*, en alguna de las siguientes versiones: Pro, Enterprise o Education(1511 November update, Build 10586 o posterior)
- Hyper-V tiene que estar habilitado. El instalador de Docker para Windows va a habilitarlo por vos si es necesario
(esto va a requerir un reinicio).


**Si tu máquina no cumple estos requerimientos seguí las instrucciones de [Docker para versiones viejas](#docker-para-versiones-viejas)**

## Docker para versiones viejas


Si tu computadora o sistema operativo no cumplen con los requerimientos (Mac anterior a 2010, Windows 7, 8, 10 no profesional), podés instalar Docker Toolbox.

[Descargá Docker Toolbox para versiones viejas de Mac](https://download.docker.com/mac/stable/DockerToolbox.pkg)


[Descargá Docker Toolbox para versiones viejas de Windows](https://download.docker.com/win/stable/DockerToolbox.exe)


Luego de instalar abrí ```Docker Quickstart Terminal```

Docker toolbox va abrir una terminal y va a crear una máquina virtual con VirtualBox para usar (puede demorar unos minutos), cuando termine, vas a ver algo así


                         ##         .
                   ## ## ##        ==
                ## ## ## ## ##    ===
            /"""""""""""""""""\___/ ===
       ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
            \______ o           __/
              \    \         __/
               \____\_______/

      The Docker Quick Start Terminal is configured to use Docker with the "default" VM.
      usuario@host ~
      $


## Docker en Linux

Docker corre de forma nativa en Linux. Según la distribución que uses, vas a correr un comando diferente.


### Ubuntu

1- Instalá los paquetes para permitir usar apt con un repositorio en HTTPS

```bash
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

2- Agrega la clave GPG de Docker

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

3- Habilitá el repositorio stable

```bash
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

4- Actualizá el índice del package manager con los paquetes del repositorio que agregamos recién

```bash
$ sudo apt-get update
```

5- Instalá la ultima versión de Docker

```bash
$ sudo apt-get install docker-ce
```


# 2. Probemos que tenemos Docker instalado

¿Ya instalaste Docker? Bueno, vamos a confirmar que esto es así.

Para esto vamos a correr nuestro primer container, el clásico y favorito "Hello, world"

Para esto ejecutamos el siguiente comando en la terminal de Docker

```bash
$ sudo docker run hello-world
```

Este comando baja una imagen de Docker con un programita embebido, instancia esta imagen (es decir,
crea un container de Docker con esa imagen) y muestra en la terminal el mensajito "Hello, world".

¿Apareció? Esperamos que sí, y si no es así, contactanos así te ayudamos a ver en dónde puede estar el problema:
* [En nuestro canal de IRC](https://kiwiirc.com/client/irc.freenode.org/#linuxchixar)
* [O por cualquiera de nuestros métodos de contacto](/contact/)

# 3. Bajemos las imágenes que vamos a usar

Vamos a bajar las imágenes de Docker de MySQL 5.7 y Wordpress.

**Es importante hacer esto en nuestras casas para no saturar la internet del taller.**

En la terminal de Docker corremos:

```bash
$ docker pull mysql:5.7
```

Cuando termine seguimos con Wordpress:

```bash
$ docker pull wordpress
```

**Para Linux**: Vas a tener que agregar ```sudo``` adelante de los comandos de Docker. Si preferís no ejecutar los comandos con sudo, seguí estos pasos (En inglés): https://docs.docker.com/engine/installation/linux/linux-postinstall/
