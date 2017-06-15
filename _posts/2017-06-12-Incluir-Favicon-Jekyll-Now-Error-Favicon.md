---
layout: post
title: "Implementar un favicon a la dirección web de un blog hecho con plantilla jekyll-now"
date: 2017-06-12
tags: [Blog, Favicon, Error, Jekyll, Solucion, Crear, Tutorial]
author: Juanjo
comment: true
---

#### Publicado por Juanjo

Al iniciar `jekyll serve` me he dado cuenta de que aparece un error en el terminal.

![alt text](https://archive.org/download/ErrorFavicon/error%20favicon.jpg)

Esto se debe a que el navegador busca un icono para mostrar en la dirección web, pero no tiene la ruta.

El problema está en que en el tema `jekyll-now` no está creada esta ruta por defecto y tenemos que hacerlo nosotros.

Lo primero que tenemos que hacer es crear el archivo `favicon.ico`. En su defecto, yo he cogido el logo del blog y lo he escalado a 55x55 pixels. Después lo he guardado como `favicon.jpg`.

Guardamos el archivo `favicon.jpg` en la carpeta /images.

Ahora vamos a editar el archivo `/_layouts/default.html` y añadiremos estas dos líneas:


```
<link rel="icon" type="image/x-icon" href="https://educandogeek.github.io/images/favicon.jpg">
<link rel="shortcut icon" href="/images/favicon.jpg">
```
Asegúrate de poner bien en la primera linea la ruta de la imagen para enlazar a la ubicación web de tu `favicon.jpg` alojado en la carpera `/images` de tu repositorio en GitHub.

Ha de quedar como muestra la siguiente imagen (he marcado de azul dónde se tienen que copiar las dos líneas):

![alt text](https://archive.org/download/FaviconSolucionDefinitiva/favicon%20solucion%20definitiva.png)

Guardamos, recargamos y ya está solucionado!

Fuentes donde he buscado la solución:

· [https://github.com/barryclark/jekyll-now/issues/536](https://github.com/barryclark/jekyll-now/issues/536)

· [https://github.com/barryclark/jekyll-now/pull/198/files](https://github.com/barryclark/jekyll-now/pull/198/files)

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1289274_1.html), [Podkas](http://www.podkas.com/directorio/educando-geek-de-jgurillo)
