---
layout: post
title: "Tutorial: Compartir una impresora convencional en internet usando Google Cloud Print"
date: 2018-02-26
tags: [Blog, Imprimir, Configuración, Compartir, Impresora, Google, Cloud, Print, Googlecloudprint]
author: Juanjo
comment: true
---

#### Publicado por Juanjo

En esta entrada os voy a dejar un tutorial elaborado a partir de diverso material recopilado en internet para:

# Compartir una impresora convencional en internet usando Google Cloud Print

Google Cloud Print es un servicio que permite imprimir desde cualquier dispositivo hacia cualquier impresora sin que estén en el mismo lugar. En este tutorial vamos a ver como usarlo desde la opción de imprimir de cualquier programa sin necesidad de pasar por el navegador.

Cabe destacar que una vez realizado, vamos a poder imprimir desde cualquier parte si tenemos conexión a Internet. Podemos estar en otra población e imprimir sin mayor problema. 

Decir que es recomendable tener instalado en navegador Google Chrome en los dispositivos des de los que queremos hacer uso de este servicio para imprimir. El no tenerlo instalado podría conllevar un mal funcionamiento o imposibilitar directamente la impresión.

![img](http://1.bp.blogspot.com/-Krwl1gHqkqM/VMqIUO_OC7I/AAAAAAAAALU/A91JMxrvMLg/s1600/google-cloud-print1.png)

Este tutorial nace de la necesidad de poder imprimir en el trabajo desde mi Chromebook Asus C202SA en una impresora que no se encuentra físicamente en mi aula.

Además, para complicar la cosa, dicha impresora no es WiFi. Es una impresora convencional de inyección de tinta, que sólo se puede conectar por cable USB a un PC. 

En concreto, un PC bastante viejo con Linux Mint Xfce. El uso de este PC es exclusivo para crear ese servidor de impresión. Se trata de un PC que estaba retirado y sin uso alguno y que ahora está en marcha para servir a tal efecto, desempeñando esta tarea de forma completamente eficiente.

Es en este momento, cuando me pongo a investigar en Internet, el cómo poder compartir dicha impresora con la casuística peculiar que acabo de describir y que además, pudiese ser reconocida por el mayor número de dispositivos posible, incluido mi Chromebook.

De toda esta investigación, nace este tutorial que redacto a modo de recordatorio para mi y también, para poder compartirlo con quien quiera que se pueda ver en esta necesidad o simplemente le pueda servir.


## Instalar la impresora

Para instalar la impresora, no ha habido mayor complicación ya que Linux Mint la ha reconocido de forma automática.

## Añadir la impresora a Google Cloud Print

Para esto necesitamos tener instalado el navegador de Chrome o su variante open source Chromium y estar logeados con una cuenta de Gmail.

Después tenemos que acceder a Google Cloud Print desde el navegador. Esto lo podemos hacer por dos vías.

- 1: vamos a justes y al final encontraremos Google Cloud Print, desde donde podremos añadir la impresora local haciendo clic en *Administrar dispositivos de Cloud Print*

- 2: Escribimos en el navegador directamente *chrome://devices*

Aquí podremos añadir, administrar y compartir de manera fácil la impresora con las personas que queramos simplemente compartiendo mediante las cuentas de Gmail que queramos que tengan acceso a esta impresora.

Una vez lanzadas las peticiones para compartirla, les llegará a estas cuentas la invitación y simplemente aceptándola ya están autorizados para hacer uso del servicio de impresión.

## Instalar el sevicio de Google Cloud Print en diferentes plataformas

A la hora de imprimir desde diferentes dispositivos, lo más fácil es hacerlo desde el navegador Chrome, pero ¿qué pasa si lo que queremos imprimir no se encuentra disponible desde Chrome, o simplemente queremos que en nuestro equipo aparezca el servivio de Google Cloud Print como una impresora más?

No os preocupéis, puesto que existen soluciones para poder conseguirlo. Concretamente, he encontrado la manera de instalar el servicio de Google Cloud Print como impresora local en equipos con Linux, Windows, Android e iOS. Desconozco si se puede hacer para Mac OS, pero estoy casi seguro de que será perfectablemente factible.

### Instalación para Linux - Ubuntu y derivadas

El proceso que describo a continuación está probado en Lliurex Linux. Una distribución derivada de Ubuntu, que la Generalitat Valenciana ha desarrollado para Centros Educativos y otras instituciones públicas de la Comunidad Valenciana, pero al ser una *Ubuntu Based*, estoy seguro de que no váis a tener problema en hacer que funcione en cualquier distribución basada en Ubuntu, como Linux Mint y similares.

Abrimos la terminal y escribimos:

```
sudo add-apt-repository ppa:simon-cadman/niftyrepo
```

```
sudo apt-get update
```

```
sudo apt-get install cupscloudprint
```

*Si aparece algún mensaje de error, lo ignoramos y seguimos escribiendo:*

```
sudo /usr/share/cloudprint-cups/setupcloudprint.py
```
En un momento dado la terminal te mostrará un link y te pedirá un código, pulsa en el link, que te abrirá el navegador web que tengas por defecto, y autoriza a la aplicación a conectarse a Google, copia el código y pega en la terminal.

Al finalizar del proceso ve al tablero y escribe impresoras, abre la aplicación y si todo va bien verás las opciones de guardar en Google Drive e imprimir en la impresora remota.



### Instalación en Windows 7 o posteriores.

Mediante esta aplicación, vamos a instalar el driver de Google Cloud Print de modo que, nos va a aparecer como una impresora más instalada en nuestro equipo y, visible desde el panel de control.

Hay que descargar el archivo virtualprintersetup.exe desde uno de los siguientes enlaces:

- Descarga desde Google Drive - [https://goo.gl/CcRvNz](https://goo.gl/CcRvNz)

-  Descarga desde Google Cloud Print Learn -
 [https://tools.google.com/dlpage/cloudprintdriver](https://tools.google.com/dlpage/cloudprintdriver)

Tan sólo tenéis que instalar el archivo virtualprintersetup.exe y reiniciar vuestra máquina con Windows para tener disponible la impresora de Google Cloud Print. Después de eso, cuando le déis a imprimir a un documento, o lo que sea, la seleccionáis y os enlazará con vuestro navegador Chrome para que podáis escoger la impresora remota conectada al servicio. Este proceso tarda unos segundos. 


### Instalación en Android

Tan sólo tenéis que instalar la aplicación oficial de Google Cloud Print desde [https://play.google.com/store/apps/details?id=com.google.android.apps.cloudprint](https://play.google.com/store/apps/details?id=com.google.android.apps.cloudprint)

### Instalación en iOS

#### Opción gratuita con Quick Print Cloud Lite

Instalar la App Quick Print Cloud Lite desde la App Store, disponible en el siguiente enlace - [https://itunes.apple.com/es/app/quick-print-cloud-lite/id887303743#?platform=ipad](https://itunes.apple.com/es/app/quick-print-cloud-lite/id887303743#?platform=ipad)

#### Opción de pago con App PrintCentral Pro

Instalar la App PrintCentral Pro desde la App Store, disponible en el siguiente enlace - [https://itunes.apple.com/es/app/printcentral-pro/id426362921?mt=8](https://itunes.apple.com/es/app/printcentral-pro/id426362921?mt=8)

Tiene un coste de 8,99€ a fecha de hoy. 


Y hasta aquí este tutorial. ¡Espero que os sirva tanto como a mi!


![img](http://www.fotonostra.com/digital/fotos/cloudprint1.jpg)


## Fuentes consultadas:

- Niftiest Software *Instalación de CUPS Cloud Print* en diferentes distribuciones GNU Linux - [https://www.niftiestsoftware.com/cups-cloud-print/](https://www.niftiestsoftware.com/cups-cloud-print/)

- Post *Google Cloud Print dispone de driver nativo para Windows* de SoftZone - [https://www.softzone.es/2013/07/23/google-cloud-print-dispone-de-driver-nativo-para-windows/](https://www.softzone.es/2013/07/23/google-cloud-print-dispone-de-driver-nativo-para-windows/)

- Descarga del driver de Google Cloud Print para Windows -
  [https://tools.google.com/dlpage/cloudprintdriver](https://tools.google.com/dlpage/cloudprintdriver)

- Aplicaciones compatibles con Google Cloud Print -  [https://www.google.com/cloudprint/learn/apps/](https://www.google.com/cloudprint/learn/apps/)

- **Desactuaizado** - Post *Imprimir en forma remota desde Ubuntu usando Google Cloud Print* de Planeta Diego - [https://planetadiego.com/2015/08/03/imprimir-en-forma-remota-desde-ubuntu-usando-google-cloud-print/](https://planetadiego.com/2015/08/03/imprimir-en-forma-remota-desde-ubuntu-usando-google-cloud-print/)

- **Desactualizado** - Post *Usar las impresoras de Google Cloud Print como locales* de DesdeLinux - [https://blog.desdelinux.net/usar-impresoras-google-cloud-print/](https://blog.desdelinux.net/usar-impresoras-google-cloud-print/)
