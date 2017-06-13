---
layout: post
title: "Creación de un blog / podcast con Jekyll"
date: 2017-06-12
tags: [Blog, Jekyll, Git, Ruby]
author: Juanjo
comment: true
---

#### Publicado por Juanjo

## Tutorial para la creación de un blog usando Jekyll


Mediante la herramienta Jekyll vamos a crear un blog que además, tendrá la posibilidad de crear la publicación de un podcast. Es decir, podremos publicar contenido escrito y además, podremos usarlo para publicar un podcast.

Para ello, vamos a necesitar de las siguientes herramientas:

· **Jekyll**: [Jekyll](https://jekyllrb.com/) es un generador estático de blogs.

· **Github**: [GitHub](https://github.com) es una plataforma de desarrollo colaborativo de software para alojar proyectos utilizando el sistema de control de versiones Git.

· **Ruby**: [Ruby](https://www.ruby-lang.org/es)

· **Archive.org**: [Archive.org](https://archive.org/) es el lugar donde vamos a poder alojar los audios de nuestro podcast, si es que tenemos pensado crearlo, de manera gratuita. También podremos guardar cualquier otro tipo de contenido.

· **Markdown**: [Markdown](https://es.wikipedia.org/wiki/Markdown) es un lenguaje de marcado con el que vamos a escribir nuestros post. Aquí encontrarás un [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) para dar los primeros pasos. Tenlo siempre a mano.

Son todo herramientas libres y gratuitas

### Paso 1. Crearnos una cuenta en GitHub y hacer un fork de jekyll-now (plantilla para el blog).

Entramos en [GitHub](https://github.com) y nos registramos. 

### Paso 2. Hacer un fork de jekyll-now

Para registrarnos en GitHub y hacer el fork, vamos a leer el post [https://devexperto.com/blog-gratis-github-jekyll](https://devexperto.com/blog-gratis-github-jekyll/) donde lo vas a encontrar todo perfectamente explicado. En este post, [Antonio Leiva](https://antonioleiva.com/) explica de manera fácil y accesible todo el proceso. Te recomiendo ver el [video](https://www.youtube.com/watch?v=lsvRyE5tPQQ&feature=youtu.be) que incluye el post.

Hacer un fork consiste en copiar un repositorio de otra persona en tu propio Github. Esto es muy útil para trastear con código de otra gente, o para hacer modificaciones.

### Paso 3. Instalar git, ruby y gemas.

###### Instalación de git y ruby

En Debian/Ubuntu y derivados:

```
sudo apt-get install git ruby jekyll
```

En fedora y derivados:

```
sudo yum install git ruby
gem install jekyll
```

En Arch y derivados:

```
sudo pacman -S git ruby
yaourt -S ruby-jekyll --noconfirm
```


###### Instalación de gemas

```
gem install jekyll bundler
gem install jekyll-sitemap
gem install jekyll-feed
```



**_Solo en distribuciones Arch (Manjaro, Antergos, etc.)_**

`Ahora te tienes que ir al fichero ~/.bashrc y pegar esta línea al final del fichero:`

```
PATH="$(ruby -e 'print Gem.user_dir')/bin:$PATH"
```
Guarda y reinicia la terminal.

###### Configuración base.

Configuramos git con nuestros datos de GitHub

```
git config --global user.email "email_id"
git config --global user.name "nombre_usuario"
```

### Paso 4. Clonar nuestro repositorio para trabajar en local

Ahora vamos configurar nuestro PC para poder subir a nuestros repositorios en GitHub, todo aquello que hagamos en local mediante la terminal.

###### Generar tu clave pública SSH

Para comenzar, primero borraremos las posibles ssh creadas, para ello entramos en ~/.ssh y eliminaremos los ficheros *_rsa y *.pub que haya.

Cuando lo hagas ejecuta el comando:

```
ssh-keygen
```

Saldrán una serie de preguntas. puedes ir pulsando intro para que se respondan con valores por defecto. eso no influye.

Cuando termine, aparecerán un par de ficheros dentro de ~/.ssh/

Seguramente se llamarán id_rsa y id_rsa.pub o adquirán el nombre que has elegido si has puesto alguno en el paso anterior.

Ahora abre el fichero acabado en .pub con algún editor de textos que te permita copiar el contenido, copia el contenido y ves a [github.com](https://github.com)

![alt text](https://ugeek.github.io/img/post/github_key.png)

Si te sale lo primero, haz click sobre Use SSH y después haz click sobre el botón de copiar que hay debajo (o copia la url que te aparece debajo), si te sale lo segundo, haz click sobre el botón copiar de abajo directamente para copiar la url

Ahora ves a la terminal donde quieres importar este repositorio y escribe:

`git clone "aquí pegas lo que acabas de copiar en el portapapeles con may+ctrl+v"`

por ejemplo:

```
git@github.com:educandogeek/educandogeek.github.io.git
```

Se descargará todo el repositorio descomprimido y ya podrás trabajar en local.

Ves a tu carpeta home y comprueba que se ha creado un nuevo directorio con el proyecto.

En mi caso `/home/jgurillo/educandogeek.github.io`


### Paso 5. Ejecutar el Blog en local.

Ir al directorio raiz del proyecto. En mi caso, la orden sería

```
cd /home/jgurillo/educandogeek.github.io
```

Una vez dentro de ese directo, ejecutar la orden

```
jekyll serve
```

Para comprobar que el blog está funcionando en local ves al navegador web y introduce la siguiente dirección:

`http://localhost:4000`

Para acceder desde otro dispositivo dentro de nuestra red local, poniendo por ejemplo que el localhost o ip local de nuestro dispotivo es 192.168.1.100, ejecutar:

`jekyll serve --host 192.168.1.100`

Ya puedes empezar a modificar el contenido del blog localmente a través de tu editor de código preferido. Sirve cualquier editor de texto.


### Subir las modificaciones del blog a GitHub

· Vemos el estado desde el último cambio.

```
git status
```

· Añadimos a git todos los cambios que hemos hecho en local.

```
git add .
```

· Hacer un `commit`, que es una breve explicación del cambio o nuevo archivo que enviamos.

```
git commit -m "comentario que constará"
```

· Subir el archivo a GitHub

```
git push origin master
```

**_Si tenemos instalado GitHub en dos dispositivos, antes de editar, deberiamos verificar o descargar el contenido remoto de GitHub a local._**

**_También deberíamos verificar o descargar el contenido remoto de GitHub a local si hacemos alguna modificación desde el navegador en nuestro repositorio._**

· Para ello escribiremos en la terminal:

```
git pull origin master
```
_________

### Fuentes que he usado para realizar este post.

· Agradecimientos a Angel de uGeek en [https://ugeek.github.io](https://ugeek.github.io)

· Agradecimientos a Laura del podcast [Experimenta con Jekyll](http://feeds.feedburner.com/ExperimentaConJekyll) y [Vacia tu bandeja](http://vaciatubandeja.com)

· [https://blog.desdelinux.net/hacer-blog-jekyll](https://blog.desdelinux.net/hacer-blog-jekyll)

· [https://devexperto.com/blog-gratis-github-jekyll](https://devexperto.com/blog-gratis-github-jekyll)
