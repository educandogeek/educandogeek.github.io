---
layout: post
title: "Tutorial para montar Plex + Google Drive ilimitado + Reclone en una Raspberry Pi 3b"
date: 2019-07-10
tags: [Blog, Plex, Google Drive, RClone, Raspberry Pi 3b, jgurillo, eDucando Geek]
author: Juanjo
comment: true
---

#### Publicado por Juanjo


Este tutorial ha sido desarollado y probado en una Raspberry Pi 3b con Raspbian 9 Stretch Lite. Si tu Raspberry es un modelo mayor o estás usando una versión de Raspbian posterior pienso que no deberías tener ningún problema.

Plex Media Server es un fantástico servicio que una vez instalado en cualquier PC va a correr de manera "silenciosa e invisible" y nos va a ofrecer, gracias a RClone, la posibilidad de visionar el contenido multimedia de nuestra nube de Google Drive en cualquier dispositivo conectado a nuestra red local o remota. Así pués, vamos a disponer de una extensa biblioteca de contenido multimedia para nuestro uso y disfrute desde una pequeña y modesta Raspberry Pi 3b. Además, vamos a poder compartir con otros usuarios de Plex todo ese contenido.

El contenido de este tutorial si bien lo he escrito de la manera más detallada posible, exige que ya tengas tu Raspberry Pi 3b con Raspbian Instalado y que sepas conectarte a ella vía SSH y uso de órdenes básicas en la terminal. 

Si acabas de comprar tu Raspberry Pi 3b te recomiendo que [leas primero este otro tutorial](https://educandogeek.github.io/Notas-Raspberry-Pi-3/) donde indico cómo realizar su puesta en marcha. Tal vez sea un tutorial algo obsoleto por la versión de Raspian o el modelo de Raspberry pero te servirá de orientación.

![img](https://i.imgur.com/MK4NxeP.jpg)


#### Te invito a que escuches el podcast que acompaña este tutorial y que tienes disponible en:
[https://anchor.fm/educandogeekanchor/episodes/104-Tutorial-Plex--Google-Drive--RClone--Raspberry-Pi-e4j547](https://anchor.fm/educandogeekanchor/episodes/104-Tutorial-Plex--Google-Drive--RClone--Raspberry-Pi-e4j547)



### Instalar RClone y vincularlo a una cuenta de Google Drive

*Sobra decir que si la cuenta de Google Drive que vamos a usar es ilimitada pues mejor que mejor.*


![img](https://i.imgur.com/sQvjRrU.jpg)


**·Instalar RClone:**

```
curl https://rclone.org/install.sh | sudo bash
```

Si por lo que sea, esto no lo descarga e instala, siempre podemos realizar la descarga manual a nuestro `/home` de la versión `.deb ARM-64 Bit` para nuestra Raspberry Pi 3b desde [https://rclone.org/downloads/](https://rclone.org/downloads/)

Yo para no complicarme con la terminal (Raspbian Lite no tiene escritorio gráfico) lo que hago es meter el USB con Raspbian en mi PC de escritorio y descargar el `archivo de instalación.deb` en el `/home` de mi Raspberry.

Cuando hayamos vuelto a arrancar la Raspberry realizamos la instalación con:

```
sudo dpkg -i rclone*.deb
```

Como ya no necesitamos más ese archivo lo podemos borrar con:

```
rm rclone*.deb
```

Vamos a comprobar que RClone se ha instalado con 

```
rclone
```

#### Ahora vamos a configurar RClone para que trabaje con nuestra nube de Google Drive


Rclone dispone de un listado amplio de nubes públicas.

Para utilizar una cuenta en rclone, teclearemos en nuestra terminal:

```
rclone config
```

Ahora, entre las opciones, introduciremos **n**, para crear una nueva cuenta en Rclone:

```
e) Edit existing remote
n) New remote
d) Delete remote
r) Rename remote
c) Copy remote
s) Set configuration password
q) Quit config
e/n/d/r/c/s/q> n
```
Nos pedirá que le **pongamos un nombre** (yo le he puesto *drive*)

```
name> drive
```

Y ahora nos saldrá el gran listado de nubes públicas:

```
Type of storage to configure.
Enter a string value. Press Enter for the default ("").
Choose a number from below, or type in your own value
 1 / A stackable unification remote, which can appear to merge the contents of several remotes
   \ "union"
 2 / Alias for a existing remote
   \ "alias"
 3 / Amazon Drive
   \ "amazon cloud drive"
 4 / Amazon S3 Compliant Storage Providers (AWS, Ceph, Dreamhost, IBM COS, Minio)
   \ "s3"
 5 / Backblaze B2
   \ "b2"
 6 / Box
   \ "box"
 7 / Cache a remote
   \ "cache"
 8 / Dropbox
   \ "dropbox"
 9 / Encrypt/Decrypt a remote
   \ "crypt"
10 / FTP Connection
   \ "ftp"
11 / Google Cloud Storage (this is not Google Drive)
   \ "google cloud storage"
12 / Google Drive
   \ "drive"
13 / Hubic
   \ "hubic"
14 / JottaCloud
   \ "jottacloud"
15 / Local Disk
   \ "local"
16 / Mega
   \ "mega"
17 / Microsoft Azure Blob Storage
   \ "azureblob"
18 / Microsoft OneDrive
   \ "onedrive"
19 / OpenDrive
   \ "opendrive"
20 / Openstack Swift (Rackspace Cloud Files, Memset Memstore, OVH)
   \ "swift"
21 / Pcloud
   \ "pcloud"
22 / QingCloud Object Storage
   \ "qingstor"
23 / SSH/SFTP Connection
   \ "sftp"
24 / Webdav
   \ "webdav"
25 / Yandex Disk
   \ "yandex"
26 / http Connection
   \ "http"
```

Introducimos el número de la nube. En esta versión de RClone hay que introducir el número **12**, correspondiente a Google Drive y seguimos con el proceso.

Pregunta: `client_id>` y `client_secret>` , las dejamos por defecto en blanco pulsando Intro

Después pide el tipo de acceso: `scope>` , le doy acceso completo con el número **1** que es el acceso de lectura y escritura.

A los siguientes: root_folder_id>  y  service_account_file> las dejamos por defecto en blanco pulsando Intro

En `Edit advanced config? (y/n)`, escribimos **n**

En `Use auto config? (y/n)`, escribimos **n**

Ahora nos saltará el navegador web para que demos nuestras credenciales de acceso a la nube mediante un token que copiaremos y pegaremos en la terminal. 

Como Raspian Lite no tiene navegador web, el método más sencillo sería instalar rclone en tu PC o Portátil, conectarte a tus nubes desde él y copiar el archivo completo o la parte perteneciente a la nube que te interesa, en la configuración de rclone de tu raspberry o servidor sin interfaz gráfica.

El archivo de configuración, te recuerdo que está en: `$HOME/.config/rclone/rclone.conf`

Si optas por este método que te recomiendo, lo que verás en tu PC será esto:

![img](https://i.imgur.com/0gVnq1f.png) *Imagen de [Mosquetero Web](https://diario.mosqueteroweb.eu/2019/06/como-usar-la-nube-en-local.html)*

Introducimos **usuario** y **contraseña** de la cuenta de Google Drive.

Le damos a **conceder permisos de acceso** a Rclone a nuestro Drive y nos saldrá lo siguiente:

![img](https://i.imgur.com/cIS4kvG.png) *Imagen de [Mosquetero Web](https://diario.mosqueteroweb.eu/2019/06/como-usar-la-nube-en-local.html)*

Copiamos el token que nos proporciona Google y volvemos a la termial donde lo copiaremos mediante la combinación de teclas `Ctrl + Mayús + V`

Ahora de nuevo en la Terminal dónde sigue el rclone config

En `Configure this as a team drive?` , escribimos **n**

Y nos saldrá nuestra unidad configurada y sus parámetros:

![img](https://i.imgur.com/Td8A25Y.png)

Confirmamos escribiendo **y**

A la preguta:

```
Configure this as a team drive?
y) Yes
n) No
y/n> 
```
Respondemos **n** y nos mostrará la unidad que hemos creado:

![img](https://i.imgur.com/Y3KDO25.png)

Salimos escribiendo **q**

Ya tenemos configurada la Unidad para acceder a los archivos de la nube.



_______________

### Ahora vamos a montar la nube de Google Drive


![img](https://i.imgur.com/oE32WcM.jpg)


#### Vamos a montar la nube pública en nuestro servidor, como si fuera una unidad de disco duro. Para ello, necesitamos instalar Fuse si no lo tenemos instalado.

```
sudo apt-get install fuse
```

#### Montaremos el contenido de la nube de Google Drive en una carpeta local en nuestro `/home` para que posterioemente plex-media-server pueda añadir su contenido a las bibliotecas.

Para ello, lo primero es crear esa carpeta que yo he llamado **drive** con el mismo nombre que la nube en RClone para evitar confusiones por mi parte. Nos ubicamos en el `/home` de nuestra Raspberry y creamos la carpeta con:

```
mkdir /home/pi/drive
```

#### Permitir a usuarios no root, montar unidades y que plex tenga permiso para acceder a la carpeta montada.

Descomentamos la línea **--allow-others** en `/etc/fuse.conf

Para ello:

```
sudo nano /etc/fuse.conf
```
Quitamos **#** y lo dejamos como sigue:

```
#Allow non-root users to specify the allow_other or allow_root mount options.
--allow-others
```
Guardamos con `Ctrl + O` y salimos con `Ctrl + Q`

Hecho esto es muy conveniente reiniciar la Raspberry con `sudo reboot`



#### Ya podemos montar la nube de drive en la carpeta drive.

Lo haremos con:

```
rclone mount drive: /home/pi/drive --allow-other &
```
Podemos acceder ahora a verificar que la nube se ha montando accediendo a la carpeta /home/pi/drive y listando el contenido con un `dir`

#### Ahora vamos a configurar crontab Automontar la nube al iniciar el sistema operativo.

Lo más interesante de esto es que cada vez que arranquemos la Raspberry Pi de forma completamente automática se nos montará el contenido de la nube de Google Drive en la carpeta local que hemos llamado drive.

Para hacerlo editaremos el archivo `crontab` mediante:

```
crontab -e
```

Y al final de todo añadiremos la línea:

```
@reboot rclone mount drive: /home/pi/drive --allow-other &
```

Ya lo tenemos todo listo.


_______________

### Por último, vamos a Instalar Plex en la Raspberry Pi 3b


![img](https://i.imgur.com/vgFEdoB.jpg)



#### A fecha de hoy no se encuentra disponible el paquete de plex-media-server en los repositorios oficiales de Raspbian, así que tendremos que descargarlo desde la web oficial.

Vamos a descargar a nuestro `/home` la versión para nuestra Raspberry Pi 3b con ARM-V7 desde [https://www.plex.tv/media-server-downloads/](https://www.plex.tv/media-server-downloads/)

Yo para no complicarme con la terminal (Raspbian Lite no tiene escritorio gráfico) lo que hago es meter el USB con Raspbian en mi PC de escritorio y descargar el `archivo de instalación.deb` en el `/home` de mi Raspberry.

Como no recibiremos actualizaciones automáticas, en caso de querer actualizar Plex cuando aparezca una nueva versión tendremos que repetir este proceso.


**· Instalación:**

Realizamos la instalación con:

```
sudo dpkg -i plexmediaserver*.deb
```

Como ya no necesitamos más ese archivo lo podemos borrar con:

```
rm plexmediaserver*.deb
```

**·Establecer los permisos:**

```
sudo nano /etc/default/plexmediaserver.prev
```

Después buscar la línea

```
PLEX_MEDIA_SERVER_USER=plex
```

Borrar “plex” y cambiar por “pi”. Entoces quedaría así:

```
PLEX_MEDIA_SERVER_USER=pi
```

**· Hacer eque el servicio inicie con el sistema:**

```
systemctl enable plexmediaserver.service
```

OTRAS ÓRDENES DE INTERÉS PARA EL SERVICIO DE PLEX:


**· Consultar el estado del servicio:**

```
systemctl status plexmediaserver.service
```

**· Iniciar servicio:**

```
systemctl start plexmediaserver.service
```

**· Detener servicio:**

```
systemctl stop plexmediaserver.service
```

**· Desactivar que el servicio arranque con el sistema:**

```
systemctl disable plexmediaserver.service
```


### Gestionar Plex Media Server desde el navegador web.

Introducir la siguiente dirección en el navegador:

`http://localhost:32400/web/`

Si queremos acceder desde otro PC, introduciremos en el navegador la dirección:

`http://dirección_ip_de_la_raspberry:32400/web/index.html`




_______________


*SI PLEX NO PUEDE ACCEDER A LA CARPETA DONDE HAS MONTADO LA NUBE DE GOOGLE DRIVE ASEGÚRATE DE:*

Dar permisos a la carpeta drive

```
chmod -R 777 drive
```

Dar permisos al usuario pi a la carpeta drive

```
sudo chown pi:pi drive
```

_______________



### Opcional: Habilitar DLNA / UPNP

Una vez instalado todo y definidas las rutas para las películas, series, música, etc, es importante habilitar la opción UPNP para poder acceder a todo el contenido multimedia.

Si usamos la aplicación cliente de Plex (de pago en tablets i teléfonos), no es necesario, pero podemos usar, por ejemplo, VLC o el servicio UPNP de nuestro televisor para acceder al contenido multimedia del equipo plex media server. La mayoría de Smart TV disponen gratuitamente de Plex.

Para ello, nos dirigiremos a `ajustes / DLNA / Habilitar DLNA / Guardar cambios`



_______________

#### Ha sido un tutorial un pelín largo pero el resultado realmente merece la pena y estoy seguro que cuando te sientes en el sofá a disfrutar de esas películas y series, por supuesto copias en blanco y negro ;-) , que has subido a tu nube de Google Drive lo disfrutarás el doble por haberte montado tú mismo o tú misma todos los servicios con unos costes muy reducidos.

#### Mi próximo proyecto es montar todo esto mediante Docker, pero eso ya es otra historia ... 


_______________


### Fuentes consultadas

· [Tutorial para RClone de Angel de uGeek](https://ugeek.github.io/blog/post/2019-07-03-dale-almacenamiento-ilimitado-a-tu-raspberry-servidor-o-pc-con-rclone.html)

· [Tutorial para RClone de Pedro de Diario de @MosqueteroWeb](https://diario.mosqueteroweb.eu/2019/06/como-usar-la-nube-en-local.html)

· [Tutorial de Plex + Rclone + Google Drive de est3ban129 cloudbites](https://cloudbit.es/foro/index.php?threads/307/) 

· [eDucando Geek Blog](https://educandogeek.github.io/Plex-Media-Server/)






_______________

Si este tutorial te ha servido de ayuda no dudes en compartirlo. Si necesitas hacerme alguna consulta:

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

· Escucha el Podcast: [Spotify](https://open.spotify.com/show/6ltKhEuriuMDInIBqsDy1X?si=mdu544METr6ZewNVe9grkw), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1580544_1.html), [iTunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [Audiobip](https://audiobip.com/podcast/educando-geek/)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Pocket Casts](https://pca.st/faj2), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)
