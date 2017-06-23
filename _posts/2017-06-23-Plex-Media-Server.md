---
layout: post
title: "Instalación de Plex Media Server"
date: 2017-06-23
tags: [Blog, Plex]
author: Juanjo
comment: true
---

#### Publicado por Juanjo


Plex Media Server es un fantástico servicio que una vez instalado en cualquier PC va a correr de manera "silenciosa e invisible" y nos va a ofrecer la posibilidad de visionar el contenido multimedia de nuestro equipo en cualquier dispositivo conectado a nuestra red local. Se que es posible conseguir esto mismo con dispositivos fuera de nuestra red local, pero es con la opción de pago y algo que no he probado.

La intención de este post es más la de explicar cómo se instala que la de explorar sus funcionalidades.

### Instalación en Arch y derivados (Manjaro Linux, Antergos, etc)

Todo el proceso se hace desde la terminal.

. Instalación

```
yaourt -S plex-media-server --noconfirm
```

· Iniciar servicio

```
systemctl start plexmediaserver.service
```

· Detener servicio

```
systemctl stop plexmediaserver.service
```

· Consultar el estado del servicio

```
systemctl status plexmediaserver.service
```

· Hacer eque el servicio inicie con el sistema

```
systemctl enable plexmediaserver.service
```

· Desactivar que el servicio arranque con el sistema

```
systemctl disable plexmediaserver.service
```

· Gestionar Plex Media Server desde el navegador web. Introducir la siguiente dirección en el navegador:

`http://localhost:32400/web/`



### Instalación en Debian, Ubuntu 16.04 y derivadas

· Equipos de 64 bits

```
wget https://downloads.plex.tv/plex-media-server/1.5.5.3634-995f1dead/plexmediaserver_1.5.5.3634-995f1dead_amd64.deb
```

· Equipos de 32 bits

```
wget https://downloads.plex.tv/plex-media-server/1.5.5.3634-995f1dead/plexmediaserver_1.5.5.3634-995f1dead_i386.deb
```

· Si se quiere tener la versión más reciente, lo mejor es saltarse el paso anterior y [dirigirse a la sección de descargas en la web oficial](https://www.plex.tv/downloads/).

· Instalación. *Tiene igual si lo hemos descargado desde terminal o desde la web.*

```
sudo dpkg -i plexmediaserver*.deb
```

*Lo demás es lo mismo que para Arch*



### Habilitar DLNA / UPNP

Una vez instalado todo y definidas las rutas para las películas, series, música, etc, es importante habilitar la opción UPNP para poder acceder a todo el contenido multimedia.

Si usamos la aplicación cliente de Plex (de pago), no es necesario, pero podemos usar, por ejemplo, VLC o el servicio UPNP de nuestro televisor para acceder al contenido multimedia del equipo plex media server.

Para ello, nos dirigiremos a `ajustes / DLNA / Habilitar DLNA / Guardar cambios`



### Fuentes consultadas

· [Configurar systemctl](https://nebul4ck.wordpress.com/2015/02/27/el-comando-systemctl-administrando-systemd/)

· [Instalación de Plex Media Server en Manjaro](https://wiki.archlinux.org/index.php/Plex)

· [Instalación en Ubuntu 16.04](https://www.linode.com/docs/applications/media-servers/install-plex-media-server-on-ubuntu-16-04)




_______________

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1289274_1.html), [Podkas](http://www.podkas.com/directorio/educando-geek-de-jgurillo)
