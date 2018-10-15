---
layout: post
title: "#78 Organiza tu Telegram con una botonera"
date: 2018-10-15
categories: podcast
tags: [telegram, botonera, organizar, menu, esquema, educandogeek]
permalink: /78/
image: images/caratula.jpg
podcast_link: https://archive.org/download/78OrganizaTuTelegramConUnaBotonera/78%20Organiza%20tu%20Telegram%20con%20una%20botonera.mp3
comment: true
---

#### Publicado por Juanjo

[https://educandogeek.github.io](https://educandogeek.github.io)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/s_p2_580544_1.html)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

[Deja aquí tu comentario](https://educandogeek.github.io/78/)

<audio controls>
  <source src="{{ page.podcast_link }}" type="audio/mp3">
</audio>


[Descarga][Mp3]


##### En el capítulo de hoy:

Que Telegram nos ofrece una variedad inmensa de usos es algo innegable. La imaginación incrementa el abanico de posibilidades y al igual que yo, estoy seguro que muchos de vosotros y vosotras usáis Telegram como una nube de almacenamiento creando canales específicos para almacenar todo tipo de archivos. El problema viene cuando quieres encontrar uno de esos canales dentro de la marabunta de conversaciones, bots, grupos, canales, etc.

Por todo ello, me he dispuesto a aplicar una gran idea que ha tenido mi amigo Ivan. Se trata de crear una botonera que organice y facilite el acceso a todas esas nubes privadas que tenemos en forma de canales. Pero no solo eso. Tambien podemos organizar por categorías todo lo que queramos: canales temáticos, grupos, servicios online, etc. Cualquier cosa que se pueda enlazar dentro de Telegram e incluso fuera, se puede poner en forma de botón.

Aquí puedes ver como ha quedado mi botonera.


![img](https://i.imgur.com/3VzYqTA.png)

![img](https://i.imgur.com/1QYJMms.png)

![img](https://i.imgur.com/4gfhZTf.png)




##### Vamos con el tutorial

- Enlace al tutorial - [https://educandogeek.github.io/78/](https://educandogeek.github.io/78/)

Lo primero que tienes que hacer es crearte un canal privado para mandarte ahí la botonera y anclarlo arriba del todo de Telegram para que sea fácil de usar.

La botonera se hace con este bot @Moderadores_Bot

Te paso la plantilla mía vacia para que puedas adaptarla a tus necesidades. Añade y/o quita lo que necesites.

Sólo debes tener en cuenta que el enlace de los botones los tienes que escribir entre comillas, y el título de los botones también entre comillas.

Para que los botones aparezcan en la misma linea, tienes que hacer una línea por cada botón sin comas ni puntos al final.

Para que los botones aparezcan en lineas separadas, tienes que hacer una línea por cada botón con una coma al final.

Puedes dejar las líneas vacias que quieras para así separar visualmente la estructura de la botonera.

Mira el código de la plantilla que no es muy complicado pero si un poco entretenido.

Te recomiendo que trabajes sobre un bloc de notas y despues copies y pegues el código al bot.

Para terminar le das a compartir al canal que tu quieras. Yo he anclado ese canal con la botonera del todo de telegram para que esté lo más accesible posible.


*Quiero agradecer a mi amigo Ivan todo lo que me enseñó sobre este método para crear una botonera personalizada.*



##### CÓDIGO:

```
!inline [📍 BOTONERA TU USUARIO TELEGRAM]

" ☁️ 💾 NUBE PRIVADA TU_USUARIO ☁️ 💾 " = "@TU_USUARIO",

" 🔏 CANALES PRIVADOS 🔏 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",

"📱 Apk's" = "TU_ENLACE"
"🖥 Software" = "TU_ENLACE",
"📙 Libros ePub" = "TU_ENLACE"
"📼 Series Clásicas" = "https://t.me/seriesclasicas",
"📝 Notas" = "TU_ENLACE"
"🎤 Notas de Voz" = "TU_ENLACE",
"🎸 Música" = "TU_ENLACE"
"🔗 Enlaces" = "TU_ENLACE",

" 🌏 CANALES PÚBLICOS 🌏 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",

" 📽 CINE 📽 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"Cine Infantil" = "https://t.me/cineinfantil"
"CineNcasa" = "https://t.me/CineNcasa",
"Cinepolis" = "https://t.me/cinepolis"
"Netflix" = "https://t.me/joinchat/AAAAAE6JZyuMY_iP5MSHng",
"Cine Palomitas" = "https://t.me/joinchat/AAAAAD26FnwUbfYwUFWRig"
"Comedia Palomitas" = "https://telegram.me/joinchat/AAAAAEGuqmO_f5f_ajHZ6w",
"Cinema-Sala1" = "https://t.me/joinchat/AAAAAEKJ4SNq6R7d2sci8w"
"Solocine" = "https://t.me/SoloCine",
"Estrenos de Cine" = "https://t.me/estrenoscine"
"PelisGram" = "https://t.me/PelisGram",

" 🎞 SERIES 🎞 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"Series Palomitas" = "https://t.me/joinchat/AAAAAFKM8qmYS3xbhU6pBw"
"SeriesGram" = "https://t.me/SeriesGram",
"Sala 6" = "https://t.me/joinchat/AAAAADvo61jWvDK-j-IFpA"
"Taquilla de Series" = "https://t.me/taquilla",

" 🐠 DOCUMENTALES 🌵 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"DocusGram" = "https://t.me/DocusGram"
"Documentales Palomitas" = "https://t.me/zonadocus",

" 📚 LIBROS 📚 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"Epub En Español" = "https://t.me/joinchat/AAAAAD6tlbS_6XR0n2Y83g"
"Libros Pipo 3.0" = "https://t.me/joinchat/AAAAAE4KQ39OnwY1MGaoSA",
"El Resurgir Del Fénix" = "https://t.me/joinchat/ALbIsEGCO5WY8sxRs9Sswg"
"Librarys" = "https://t.me/joinchat/AAAAAEGR6ed2j1RSMzIU_w",
"Chemary's Kiosko" = "https://t.me/joinchat/AJAa4D4SuzbD_regum5awg"
"Libros Digital" = "https://t.me/LibrosDigital",

" 🗞 REVISTAS, PRENSA Y OTROS 🗞 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"Revistas Gold" = "https://t.me/joinchat/AAAAAEaeqKqsLqpJgTLIow"
"Revistas Premium" = "https://t.me/Revistaspremium"
"FriendsEnglish" = "https://t.me/FriendsEnglish",

" 🤖 BOTS 🤖 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"🔗 Enlazar Archivos" = "@GetPublicLinkBot"
"📖 Enviar a Kindle" = "@to_kindle_bot",
"🔎 Buscar en Youtube" = "@vid"
"⬇️ Descargar de Youtube" = "@utubebot",
"🔎 👂 ⬇️ Buscar, Escuchar y Descargar desde Youtube" = "@vkm_bot",
"📦 Mi Tracking" = "@MiTrackingBot"
"🎞 MisSeries" = "@MisSeriesBot",

" 🎙 PODCASTS 🎙 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"eDucando Gek" = "https://t.me/educandogeek"
"Leyendo Voy" = "https://t.me/joinchat/AAAAAE3NFx5Hh6b5dhkISw",

" 🌐 SERVIDOR RASPBERRY PI 🌐 " = "ENLACE_A_TU_CANAL_CON_EL_MENU",
"⏯ Plex" = "TU_ENLACE"
"🔄 Resilio" = "TU_ENLACE"
"🔁 Syncthing" = "TU_ENLACE",

"🗣 COMPARTIR 🤝" = "SHARE",
```





##### Enlaces citados en el capítulo:

- Enlace al bot para hacer la botonera - [https://t.me/@Moderadores_Bot](https://t.me/@Moderadores_Bot)

- Enlace al tutorial - [https://educandogeek.github.io/78/](https://educandogeek.github.io/78/)

- Enlace al videotutorial de cómo hacer la botonera - [https://youtu.be/xG_BKnLRT1s](https://youtu.be/xG_BKnLRT1s)

_______________

*Recordaros también que si os gustan los libros y la lectura, tenéis disponible mi otro podcast donde encontraréis reseñas de todos los libros que voy leyendo. Sin espoilers y con una duración cortita de entre 5 y 10 minutos. Lo podéis encontrar bajo el nombre de Leyendo Voy en las plataformas de iTunes, Anchor, iVoox y Spreaker, o añadiendo manualmente el siguiente feed [http://feeds.feedburner.com/leyendovoy](http://feeds.feedburner.com/leyendovoy)*

_______________

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)





[Mp3]: https://archive.org/download/78OrganizaTuTelegramConUnaBotonera/78%20Organiza%20tu%20Telegram%20con%20una%20botonera.mp3
