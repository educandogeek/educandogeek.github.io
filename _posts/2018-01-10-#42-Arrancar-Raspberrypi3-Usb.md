---
layout: post
title: "#42 Arrancar Raspberry Pi 3 desde memoria USB - Elección de disco duro"
date: 2018-01-10
categories: podcast
tags: [Podcast, Raspberry, Pi, 3, Memoria, USB, Disco, Duro, Hdd, Arrancar]
permalink: /42/
image: images/caratula.jpg
podcast_link: https://archive.org/download/42ArranqueUsbRaspberrypi3/42-arranque-usb-raspberrypi3.mp3
comment: true
---

#### Publicado por Juanjo

[https://educandogeek.github.io](https://educandogeek.github.io)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1289274_1.html)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

[Deja aquí tu comentario](https://educandogeek.github.io/42/)

<audio controls>
  <source src="{{ page.podcast_link }}" type="audio/mp3">
</audio>


[Descarga][Mp3]


En el capítulo de hoy:

# Cómo arrancar nuestra Raspberry Pi 3 desde una memoria USB y también, elección de disco duro para almacenar grandes cantidades de información.


![img](https://media.aws.alkosto.com/media/catalog/product/cache/6/image/69ace863370f34bdf190e4e164b6e123/2/2/22265347409-toshiba-usb2-flash-1.jpg)


### ¿Qué necesito?

- Raspberry Pi 3
- Tarjeta SD (solo durante la instalación)
- Memoria USB

### Instalar tu Raspberry Pi desde una SD

Para empezar, tendrás que instalar Raspbian o Raspbian Lite en tu Pi desde una tarjeta SD. ¿Pero no dijimos que no necesitaríamos una SD? El caso es que la opción de arrancar tu Sistema Operativo desde USB viene deshabilitada de fábrica. Esta opción tiene que ser configurada en una memoria OTP (programable una vez). A partir de que hagas esta configuración tu Raspberry Pi será capaz de arrancar siempre desde USB, aunque no te preocupes, podrás arrancar el Sistema Operativo también desde la tarjeta SD.

### Actualizar tu Raspberry Pi

Si tienes una versión de Raspbian posterior al 10 de Abril de 2017, este paso no será necesario. De lo contrario, ejecuta:

```
sudo apt-get update && sudo apt-get upgrade
```

### Actualizar el firmware de la Raspberry Pi

```
sudo rpi-update
```

### Configurar el modo USB Boot

Ejecuta el siguiente comando en tu terminal:

```
echo program_usb_boot_mode=1 | sudo tee -a /boot/config.txt
```
Con esto hemos preparado el fichero de configuración de arranque para hacer la operación. Para programar el sector de arranque, reinicia:

```
sudo reboot
```
Tras  reiniciar, comprueba que lo has configurado bien con el siguiente comando:

```
vcgencmd otp_dump | grep 17:
```
Justo en la línea de debajo tienes que ver el siguiente valor:

```
17:3020000a
```

Comprueba que ese sea el valor que aparece. Si no, tendrás que revisar los pasos porque algo ha fallado.

## Instalar el Sistema Operativo en una memoria USB

Sigue los pasos de esta guía [Raspberry Pi: primeros pasos](https://www.nociones.de/raspberry-pi-primeros-pasos/) para instalar el sistema operativo. Sencillamente, en lugar de utilizar una tarjeta SD, instálalo en una memoria USB.

### ¿Problemas?

Existen algunas memorias USB que no son capaces de arrancar esta configuración. En ocasiones las memorias o discos tardan en arrancar demasiado, o utilizan un protocolo especial que tu RPi no es capaz de gestionar. En ese caso, trata de usar una de los modelos recomendados por que el equipo de la Raspberry Pi:

- Toshiba 8GB
- Sandisk Cruzer Fit 16GB
- Sandisk Cruzer Blade 16Gb
- Samsung 32GB USB 3.0 drive
- MeCo 16GB USB 3.0

![img](https://www.raspberrypi.org/app/uploads/2012/03/RPi-Logo-Reg-SCREEN-199x250.png)

Fuente: [https://www.nociones.de/como-arrancar-la-raspberry-pi-3-desde-un-usb/](https://www.nociones.de/como-arrancar-la-raspberry-pi-3-desde-un-usb/)






· Correo del programa: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

Recordaros también que si os gustan los libros y la lectura, tenéis disponible mi otro podcast donde encontraréis reseñas de todos los libros que voy leyendo. Sin espoilers y con una duración cortita de entre 5 y 10 minutos. Lo podéis encontrar bajo el nombre de Leyendo Voy en las plataformas de iTunes, Anchor, iVoox y Spreaker, o añadiendo manualmente el siguiente feed [http://feeds.feedburner.com/leyendovoy](http://feeds.feedburner.com/leyendovoy)



[Mp3]: https://archive.org/download/42ArranqueUsbRaspberrypi3/42-arranque-usb-raspberrypi3.mp3
