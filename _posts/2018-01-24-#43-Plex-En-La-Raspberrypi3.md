---
layout: post
title: "#43 Plex Media Server en mi Raspberry Pi 3 y otros servicios que uso"
date: 2018-01-24
categories: podcast
tags: [Podcast, Raspberry, Pi, 3, Resilio, Syncthing, Plex, Samba]
permalink: /43/
image: images/caratula.jpg
podcast_link: https://archive.org/download/43PlexEnRaspberrypi/43-plex-en-raspberrypi.mp3
comment: true
---

#### Publicado por Juanjo

[https://educandogeek.github.io](https://educandogeek.github.io)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1289274_1.html)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

[Deja aquí tu comentario](https://educandogeek.github.io/43/)

<audio controls>
  <source src="{{ page.podcast_link }}" type="audio/mp3">
</audio>


[Descarga][Mp3]


En el capítulo de hoy:

Qué servicios tengo instalados en mi Raspberry Pi 3 B: samba, resilio, syncthing y plex media server.

![img](https://image.roku.com/developer_channels/prod/2c2ccf2ef5997ebe154505db00c58b3cfc129b28b07cad0f7c322a077561f7c5.png)

## Instalar Plex Media Server en Raspbian 9 stretch

### Añadir el repositorio dev2day

```
wget -O - https://dev2day.de/pms/dev2day-pms.gpg.key | sudo apt-key add -
```

### Añadir el source.list

```
echo "deb https://dev2day.de/pms/ stretch main" | sudo tee /etc/apt/sources.list.d/pms.list
```

### Actualizar

```
sudo apt-get update
```

### Descargar Plex

```
sudo apt-get install -t stretch plexmediaserver-installer
```

### Establecer los permisos

```
sudo nano /etc/default/plexmediaserver.prev
```
Después buscar la línea

```
PLEX_MEDIA_SERVER_USER=plex
```
Borrar "plex" y cambiar por "pi". Entoces quedaría así:

```
PLEX_MEDIA_SERVER_USER=pi
```

### Reniciar el servicio.

```
sudo service plexmediaserver restart
```

### Acceder al servidor Plex de la Raspberry desde otro equipo.

En el navegador, escribir (poner la IP de la raspberry) 

```
ip de la raspberry:32400/web/index.html
```

_Fuente_ 
[https://thepi.io/how-to-set-up-a-raspberry-pi-plex-server/](https://thepi.io/how-to-set-up-a-raspberry-pi-plex-server/)
[https://www.raspberrypi.org/




· Correo del programa: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

Recordaros también que si os gustan los libros y la lectura, tenéis disponible mi otro podcast donde encontraréis reseñas de todos los libros que voy leyendo. Sin espoilers y con una duración cortita de entre 5 y 10 minutos. Lo podéis encontrar bajo el nombre de Leyendo Voy en las plataformas de iTunes, Anchor, iVoox y Spreaker, o añadiendo manualmente el siguiente feed [http://feeds.feedburner.com/leyendovoy](http://feeds.feedburner.com/leyendovoy)



[Mp3]: https://archive.org/download/43PlexEnRaspberrypi/43-plex-en-raspberrypi.mp3
