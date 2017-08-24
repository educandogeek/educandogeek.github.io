---
layout: post
title: "Qué hacer después de instalar Manjaro"
date: 2017-08-24
tags: [Blog, Manjaro, Configuración]
author: Juanjo
comment: true
---

#### Publicado por Juanjo

En esta entrada os voy a dejar las notas que he ido confeccionando después de instalar Manjaro. Seguramente muchas de las cosas que hay aquí apuntadas no os sean útiles, ya que se trata de lo que yo necesitaba instalar y configurar, pero estoy seguro que váis a encontrar enlaces y notas útiles.

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRuAkjh3X6le17B1bKlMnlh6W2bCCKiYeE0UAT0NvWI3juq3_a5ng)


## 01 Instalar Manjaro - Acer Aspire M1641

- Hay que arrancar el LiveUSB con el modo de: Controladores no libres


## 02 Optimizar mirrors y guía de comandos básicos de Pacman y Yaourt

```
sudo pacman-mirrors -g
```

- Comandos básicos de Pacman: [http://sobrebits.com/guia-de-comandos-basicos-de-pacman-en-archlinux-y-derivadas/](http://sobrebits.com/guia-de-comandos-basicos-de-pacman-en-archlinux-y-derivadas/) | [http://www.taringa.net/posts/linux/16548087/Uso-basico-del-comando-Pacman-Manjaro-y-basados-en-Arch.html](http://www.taringa.net/posts/linux/16548087/Uso-basico-del-comando-Pacman-Manjaro-y-basados-en-Arch.html)

- Comandos básicos de Yaourt: [https://linuxgnublog.org/es/comandos-basicos-yaourt-en-archlinux/](https://linuxgnublog.org/es/comandos-basicos-yaourt-en-archlinux/)

## 03 Instalar desde Añadir/Quitar software

- Ubuntu Fonts (fuentes de Ubuntu)
- Arc GTK Theme (tema Arc)
- Arc Firefox Theme (tema Arc para Firefox)
- Screenfetch (nos informa de nuestro sistema con la orden `screenfetch` en la terminal)
- Image Writer (para quemar isos en memorias usb)
- Etcher (para quemar isos en memorias usb)
- Plank (dock de aplicaciones)
- KeePassX2 (gestor de contraseñas)
- Dropbox (nube de archivos)
- Transmission GTK (gestor de Torrents)
- Wine (para poder instalar programas de windows)
- Yaourt (para poder instalar paquetes de Aur)
- Retext (para escribir en Markdown)

Podemos instalar todo de golpe desde la terminal concatenando los paquetes con la siguiente orden. Copia y pega en la terminal y borra los paques que no quieras instalar. Después pulsa enter.

```
sudo pacman -S ttf-ubuntu-font-family arc-gtk-theme arc-firefox-theme screenfetch imagewriter etcher plank keepassx2 dropbox transmission-gtk wine yaourt retext
```


## 04 Instalar HP Deskjet 2540

1. Iniciar sesion en el equipo como root.
2. En el navegador escribir
localhost:361
3. Administration
4. Add Printer
5. Escoger
Local Printers
HP Printer (HPLIP) 
Continue
6. Connection rellenar la casilla con:
socket://192.168.1.114:9100
7. Seguir eligiendo la configuración.
8. Si es necesario instalar manjaro-printer desde gestor de software


## 05 Configurar Terminal

- Ubuntu Font
- Quitar barra de desplazamiento


## 06 Configurar Firefox

- En la carpeta personal, activar carpetas ocultas y renombrar la carpeta chrome a chrome.oldbackup en `.mozilla/firefox/manjaro.default/`


## 07 Instalar idiomas

- Desde Gestor de configuración de Manjaro


## 08 Configurar NVIDIA X Server Settings (ya no es necesario)

- Copiar el archivo que se encuentra guardado en la carpeta: `/media/datos/Jgurillo/NVIDIA Config Manjaro/90-mhwd.conf ` a la carpeta: `/etc/X11/xorg.conf.d/`
- Necesitaremos hacerlo con Thunar Root


## 09 Configurar atajos de teclado

- **Impr Pant:**

    1 Antes de nada necesitas tener el paquete xfce4-screenshooter instalado.

    2 > Configuración> Teclado> Atajos de Aplicación> Añadir>: xfce4-screenshooter y asignar la tecla correspondiente.

- **Volumen +:**

    - amixer sset Master playback 5%+

- **Volumen -:**

    - amixer sset Master playback 5%-


## 10 Instalar Spotify

```
yaourt -S spotify --noconfirm
```


## 11 Sincronizar la hora del sistema si es necesario

- Primero comprobamos nuestra zona horaria, para ello escribimos lo siguiente en una terminal:

```
timedatectl list-timezones
```

En mi caso, estoy en España, con lo cual me corresponde la que dice "Europe/Madrid". Entonces, en la terminal ejecuté lo siguiente:

```
timedatectl set-timezone Europe/Madrid
```

- Por último, reemplazamos en el archivo /etc/adjtime la palabra "UTC" (Tiempo Universal Coordinado) por "Local" sin las comillas. En la terminal, ejecutamos:

```
sudo nano /etc/adjtime
```

Reemplazamos UTC por Local y presionamos Ctrl+o para guardar los cambios y Crtl+x para salir.

En mi caso no fue necesario reiniciar, luego de 1 o 2 minutos me quedó la hora sincronizada. Ya van un par de días de ésto e incluso apagué la máquina en varias oportunidades y no volvió a adelantarse.

Fuente: [http://hayardillasenlared.blogspot.com.es/2013/11/sincronizar-la-hora-en-manjaro-linux.html](http://hayardillasenlared.blogspot.com.es/2013/11/sincronizar-la-hora-en-manjaro-linux.html)


## 12 Configurar Plank

- En Configuración > Sesión e inicio: añadir Plank. La orden es **plank**

- Si observamos una linea en la pantalla al iniciar Plank, lo podemos corregir con: Ajustes del gestor de ventanas
    - Compositor
    - Desactivar "Mostrar sombra bajo ventanas empotrables"


## 13 Instalar YNAB4

- Una vez instalado Wine, descargamos YNAB4.exe y con el botón derecho le damos a abrir con Wine.
- La clave de activación es **J46297JBS4JS5**


## 14 Ajustar brillo del monitor des la terminal (sólo cuando las teclas dedicadas en el portátil no responden)

- Cambiar el valor 5 por un número del 1 al 10 desde la terminal con la siguiente orden.

```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

Fuente:  [http://www.taringa.net/posts/linux/17139143/Applet-para-controlar-brillo-de-pantalla-en-XFCE.html](http://www.taringa.net/posts/linux/17139143/Applet-para-controlar-brillo-de-pantalla-en-XFCE.html)

- Para **automatizar esta tarea, podemos crear un alias**:

Para crear atajor de órdenes en el terminal que se guardan en /home/jgurillo/.bashrc

Se copian al final del archivo y se guarda.

```
alias b1="echo 1 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b2="echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b3="echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b4="echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b5="echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b6="echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b7="echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b8="echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b9="echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness"
alias b10="echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness"
```

Fuente: [http://felinfo.blogspot.com.es/2011/12/creacion-y-uso-de-alias-de-comandos.html](http://felinfo.blogspot.com.es/2011/12/creacion-y-uso-de-alias-de-comandos.html)


## 16 Reparar claves públicas para Spotify

- Si tienes problema con el llavero de seguridad sigue esos pasos cambiando el llavero en conflicto

Importa la clave del programa a instalar

```
gpg --recv-keys  5CC908FDB71E12C2
```
Después la autenticarás

```
gpg --edit-key 5CC908FDB71E12C2
```
Ahora en el prompt escribe `trust`

```
gpg> trust
```
Te pregutará que intruduzcas el nivel de confianza. Puedes por ejemplo poner 5 si es que confías plenamente en ese paquete. Yo he puesto 3. Confirma la elección y por último sal de la configuración. 

```
gpg> quit
```
Ahora ya podrás compilar e instalar el paquete verificando las fuentes.

Yo he tenido que hacer lo mismo con la clave pública D9C4D26D0E604491


## 17 Instalar Redshift (protector nocturno de la radiación azul de la pantalla)

- Los valores por defecto para la vila que pongo yo en Configuración/sesión e inicio/Autoarranque de aplicaciones/Orden

```
redshift-gtk -l 38.5080:-0.2286 -t 6500:3500 -g 0.8 -m vidmode -v
```

Personalmente sólo uso esta otra orden más corta, ya que lo de detrás no es necesario

```
redshift-gtk -l 38.5080:-0.2286 -t 6500:3500
```

Fuente: [http://manjaro-es.org/viewtopic.php?f=9&t=1138](http://manjaro-es.org/viewtopic.php?f=9&t=1138)

Para saber la loongitud y latitud de tu pueblo/ciudad: [https://justgetflux.com/map.html](https://justgetflux.com/map.html)


## 18 Ajustar la fuente y el color de la hora del panel

- Por defecto a mi me parece demasiado pequeña, así que la he modificado haiendo clic con el botón derecho del ratón encima de la hora > Propiedades > Opciones del reloj > Formato personalizado

- Escribir el siguiente formato:

```
<span color="#FFFFFF" font="Noto Sans Bold 14"> %R </span>
```

## 20 Cambiar la contraseña de Usuario y Root (pede que con el tiempo queramos cambiarla)

[https://lamiradadelreplicante.com/2017/06/26/manjaro-y-antergos-aconsejan-cambiar-contrasenas/](https://lamiradadelreplicante.com/2017/06/26/manjaro-y-antergos-aconsejan-cambiar-contrasenas/)


## 21 Optimizar el renderizado de fuentes

[https://salmorejogeek.com/2016/09/02/consigue-un-renderizado-de-fuentes-perfecto-en-tu-distro-linux/](https://salmorejogeek.com/2016/09/02/consigue-un-renderizado-de-fuentes-perfecto-en-tu-distro-linux/)


## 22 Limpiar Manjaro

- **Limpiar paquetes huérfanos**

Los paquetes huérfanos son aquellos que ningun programa que tenemos instalado los necesita.

Si queremos ver si tenemos paquetes de ese tipo antes de eliminarlos podemos ejecutar el siguiente comando:

```
pacman -Qtdq
```

Y si pensamos que podemos prescindir de ellos podremos borrarlos con el comando:

```
sudo pacman -Rs $(pacman -Qtdq)
```

Si muestra el mensaje "error: no se especificaron objetivos" es probable que se deba a que no tienes paquetes huérfanos, utiliza el comando de consulta para verificarlo. 

- **Limpiar la caché de paquetes descargados que no han sido instalados**

Comando:

```
sudo pacman -Sc
```

FUENTE: [https://www.taringa.net/post/linux/16548087/Uso-basico-del-comando-Pacman-Manjaro-y-basados-en-Arch.html](https://www.taringa.net/post/linux/16548087/Uso-basico-del-comando-Pacman-Manjaro-y-basados-en-Arch.html)


# 23 Instalar Telegram

- [https://desktop.telegram.org/](https://desktop.telegram.org/)









