---
layout: post
title: "#85 Linux y LibreOffice en mi Chromebook - Tutorial"
date: 2019-02-07
categories: podcast
tags: [Chromebook, Linux, GNU, LibreOffice, instalar, usar, educandogeek, podcast]
permalink: /85/
image: images/caratula.jpg
podcast_link: https://archive.org/download/85LinuxYLibreOfficeEnMiChromebook/85%20Linux%20y%20LibreOffice%20en%20mi%20Chromebook.mp3
comment: true
---

#### Publicado por Juanjo

[https://educandogeek.github.io](https://educandogeek.github.io)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1580544_1.html)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

[Deja aquí tu comentario](https://educandogeek.github.io/85/)

<audio controls>
  <source src="{{ page.podcast_link }}" type="audio/mp3">
</audio>


[Descarga][Mp3]





##### En el capítulo de hoy:


Voy a habilitar la opción de correr una máquina virtual con Linux de forma nativa en mi Chromebook Asus C202. No olvidemos que es un equipo que me costó 100€ y que a día de hoy está corriendo App's Android y es capaz de correr aplicaciones de Linux de forma nativa.


![img](https://i.imgur.com/CPrnlzM.png)


La implementación de Linux en los Chromebooks ha traído nueva vida a nuestros equipos.

En mi caso, uso el Chromebook principalmente para mi trabajo y con tareas ofimáticas. La necesidad de poder trabajar nativamente con documentos con formato libre .odt (LibreOffice) hacía que si bien, la conversión al formato Google Docs fuese aceptable para trabajar, no era lo más cómodo para mi trabajo. Una cosa es manejar tú sólo los archivos y otra es que los estás compartiendo con otras personas que trabajan con LibreOffice.

Es por esto, que en cuanto vi que mi equipo era capaz de virtualizar esa máquina de Linux me lancé de cabeza a habilitarlo.


#### Tutorial para habilitar Linux e instalar LibreOffice en el Asus C202 Chromebook


1.- Habilitamos y activamos la máquina virtual de Linux en nuestro Chromebook desde los ajustes del sistema.

2.- Una vez se han descargado los paquetes y nos aparece la terminal en pantalla, procedemos a actualizar el sistema:

```
sudo apt upgrade
sudo apt update
```

3.- Instalamos LibreOffice con:

```
sudo apt install libreoffice
```

4.- Instalamos el paquete de idioma español para LibreOffice:

```
sudo apt install libreoffice-l10n-es
```

5.- Ejecutamos LibreOffice:

```
libreoffice
```

6.- Vamos a 

`Tools`

`Options`

`Language Settings`

`Languages`

`User Interface`

`Spanihs`

Le damos a `OK` y a `Restart Now`


7.- Modificamos la apariencia de LibreOffice. Por defecto las fuentes son demasiado pequeñas y lo mismo pasa con los iconos. Vamos a


`Herramientas`

`Opciones`

`Ver`

Ahi dentro escogemos la `Escala al 150%` y el `Tamaño de los iconos Grande`


Y listo. ¡Ya tenemos LibreOffice instalado de forma nativa en nuestro Chromebook!







##### Enlaces citados en el capítulo:


· Podcast de HardwareAdictos donde habla del funcionamiento de Linux en los Chromebooks - [https://pca.st/Ecq5](https://pca.st/Ecq5)



_______________

*Recordaros también que si os gustan los libros y la lectura, tenéis disponible mi otro podcast donde encontraréis reseñas de algunos de los libros que voy leyendo. Sin espoilers y con una duración cortita de entre 5 y 10 minutos. Lo podéis encontrar bajo el nombre de Leyendo Voy en las plataformas de iTunes, Anchor, iVoox y Spreaker, o añadiendo manualmente el siguiente feed [http://feeds.feedburner.com/leyendovoy](http://feeds.feedburner.com/leyendovoy)*






_______________

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)



[Mp3]: https://archive.org/download/85LinuxYLibreOfficeEnMiChromebook/85%20Linux%20y%20LibreOffice%20en%20mi%20Chromebook.mp3
