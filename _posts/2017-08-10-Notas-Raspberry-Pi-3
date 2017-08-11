---
layout: post
title: "Notas de instalación de servicios en Raspberry Pi 3 con Raspbian Litle"
date: 2017-08-10
tags: [Blog, Raspberry, Hdmi, Raspbian, Ssh, Temperatura, Alias, Resilio, Syncthing, Samba, Plex]
author: Juanjo
comment: true
---

#### Publicado por Juanjo

# Raspbian

## Login y Password por defecto en Raspbian

Login: **pi**

Password: **raspberry**

## Solucionar problema HDMI sin señal

Editar el archivo `config.txt` que encontraremos en `/boot` y descomentar la linea que dice `hdmi_safe=1` *tal como muestra la siguiente captura.*

![image](https://archive.org/download/CapturaDePantalla20170720134043/Captura%20de%20pantalla_2017-07-20_13-40-43.png)

## Configurar Raspbian

Para acceder a la configuración, teclearemos en la terminal

```
sudo raspi-config
```
### Localisation options

`Change locale` / `es_ES.UTF-8 UTF-8`

`Change timezone` / `Europa` / `Madrid`

### Advanced options

`Expand Filesistem` / *para usar toda la memoria SD*

`SSH` / *para activar el acceso por SSH*

## Conexión por SSH

Poner en una terminal 

```
ssh pi@192.168.1.103
```
Aceptar el certificado con `yes`

## Saber temperatura de la Raspberry Pi

_Para saber la temperatura de la CPU (procesador):_

```
cat /sys/class/thermal/thermal_zone0/temp
```
Lo que nos mostrará algo como esto

**_50843_**

Que no es otra cosa que *50’843* Cº (hay que dividir entre 1000)


_Para saber la temperatura de la GPU (chip gráfico)_

```
vcgencmd measure_temp
```

Que en mi ejemplo me ha dado

**_temp=50.8’C_**

*Fuente* - [http://alteageek.homelinux.org/?page_id=1042](http://alteageek.homelinux.org/?page_id=1042)

## Alias en .bash

Podemos crear alias para que simplemente escribiendo una palabra en la terminal se ejecuten comandos específicos. Para ello:

```
sudo nano /home/pi/.bashrc
```
añadir al final del archivo los alias que nos interesen copiando y pegando:

### Alias temp para mostrar la temperatura de la Raspberry

```
alias temp='cat /sys/class/thermal/thermal_zone0/temp && vcgencmd measure_temp&& echo "Lectura de temperatura finalzada. 1ª=procesador 2ª=gráfica"'
```

### Alias para apagar la Raspberry

```
alias apagar='sudo poweroff && echo "Apagando"'
```

### Alias para reiniciar la Raspberry 

```
alias reiniciar='sudo reboot && echo "Reiniciando"'
```

guardamos, reiniciamos y ya funcionarán.

## Instalar Resilio

1- Añadimos los repositorios:

```
echo "deb http://linux-packages.resilio.com/resilio-sync/deb resilio-sync non-free" | sudo tee /etc/apt/sources.list.d/resilio-sync.list
```

2- Añadimos la clave pública con este comando:

```
wget -qO - https://linux-packages.resilio.com/resilio-sync/key.asc | sudo apt-key add -
```

En su defecto tambien podemos usar este otro comando (el que yo he usado)

```
curl -LO https://linux-packages.resilio.com/resilio-sync/key.asc && sudo apt-key add ./key.asc
```

2- Actualizamos el repositorio:

```
sudo apt update
```

3- Instalamos Resilio

```
sudo apt-get install resilio-sync
```

4- Hacemos que resilio arranque con el sistema

```
sudo systemctl enable resilio-sync
```

5- otros comandos que se pueden necesitar serian:

```
sudo systemctl stop resilio-sync
sudo systemctl start resilio-sync
sudo systemctl restart resilio-sync
sudo systemctl status resilio-sync
```

Ahora escribimos localhost:8888 y entraremos en la interfaz web de resilio.

Para entrar desde otro equipo escribimos 192.168.1.103:8888

## Instalar Syncthing

Añadimos el repositorio

```
curl -s https://syncthing.net/release-key.txt | sudo apt-key add -

sudo echo "deb https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list
```

Actualizamos los repositorios y comenzamos la instalación

```
sudo apt-get update 

sudo apt-get install syncthing
```

Si queremos acceder desde otro dispositivo a la interfaz web de Syncthing, dentro de nuestra red local, es editar un archivo de configuración mediante SSH. Introduciremos esta línea en la Terminal y añadiremos la ip de nuestra Raspberry Pi, en lugar de 127.0.0.1.

```
sudo nano ~/.config/syncthing/config.xml
```

Cambiamos aquí la IP y ponemos la nuestra `192.168.1.103`

```
<gui enabled="true" tls="false">
    <address>127.0.0.1:8384</address>
</gui>
```

Ahora creamos un script:

```
sudo nano /etc/init.d/syncthing
```

Copiamos esto:

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          Syncthing
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Syncthing
# Description:       Syncthing is for backups
### END INIT INFO
 
 
# Documentation available at
# http://refspecs.linuxfoundation.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/iniscrptfunc.html
# Debian provides some extra functions though
. /lib/lsb/init-functions
 
 
DAEMON_NAME="syncthing"
DAEMON_USER=pi
DAEMON_PATH="/usr/bin/syncthing"
DAEMON_OPTS=""
DAEMON_PWD="${PWD}"
DAEMON_DESC=$(get_lsb_header_val $0 "Short-Description")
DAEMON_PID="/var/run/${DAEMON_NAME}.pid"
DAEMON_NICE=0
DAEMON_LOG='/var/log/syncthing'
 
[ -r "/etc/default/${DAEMON_NAME}" ] && . "/etc/default/${DAEMON_NAME}"
 
do_start() {
  local result
 
	pidofproc -p "${DAEMON_PID}" "${DAEMON_PATH}" > /dev/null
	if [ $? -eq 0 ]; then
		log_warning_msg "${DAEMON_NAME} is already started"
		result=0
	else
		log_daemon_msg "Starting ${DAEMON_DESC}" "${DAEMON_NAME}"
		touch "${DAEMON_LOG}"
		chown $DAEMON_USER "${DAEMON_LOG}"
		chmod u+rw "${DAEMON_LOG}"
		if [ -z "${DAEMON_USER}" ]; then
			start-stop-daemon --start --quiet --oknodo --background \
				--nicelevel $DAEMON_NICE \
				--chdir "${DAEMON_PWD}" \
				--pidfile "${DAEMON_PID}" --make-pidfile \
				--exec "${DAEMON_PATH}" -- $DAEMON_OPTS
			result=$?
		else
			start-stop-daemon --start --quiet --oknodo --background \
				--nicelevel $DAEMON_NICE \
				--chdir "${DAEMON_PWD}" \
				--pidfile "${DAEMON_PID}" --make-pidfile \
				--chuid "${DAEMON_USER}" \
				--exec "${DAEMON_PATH}" -- $DAEMON_OPTS
			result=$?
		fi
		log_end_msg $result
	fi
	return $result
}
 
do_stop() {
	local result
 
	pidofproc -p "${DAEMON_PID}" "${DAEMON_PATH}" > /dev/null
	if [ $? -ne 0 ]; then
		log_warning_msg "${DAEMON_NAME} is not started"
		result=0
	else
		log_daemon_msg "Stopping ${DAEMON_DESC}" "${DAEMON_NAME}"
		killproc -p "${DAEMON_PID}" "${DAEMON_PATH}"
		result=$?
		log_end_msg $result
		rm "${DAEMON_PID}"
	fi
	return $result
}
 
do_restart() {
	local result
	do_stop
	result=$?
	if [ $result = 0 ]; then
		do_start
		result=$?
	fi
	return $result
}
 
do_status() {
	local result
	status_of_proc -p "${DAEMON_PID}" "${DAEMON_PATH}" "${DAEMON_NAME}"
	result=$?
	return $result
}
 
do_usage() {
	echo $"Usage: $0 {start | stop | restart | status}"
	exit 1
}
 
case "$1" in
start)   do_start;   exit $? ;;
stop)    do_stop;    exit $? ;;
restart) do_restart; exit $? ;;
status)  do_status;  exit $? ;;
*)       do_usage;   exit  1 ;;
esac
```


Damos poderes de ejecución

```
sudo chmod +x /etc/init.d/syncthing
```

Habilitamos que inicie cada vez que reiniciemos

```
sudo update-rc.d syncthing defaults
```

Ahora podemos iniciar así

```
sudo service syncthing start
```

Abrimos el navegador y para acceder a la interfaz web escribiremos `192.168.1.103:8384`


Fuente:

[https://ugeek.github.io/049.-Instalando-Syncthing-en-ubuntu-antergos-y-rapsberry/](https://ugeek.github.io/049.-Instalando-Syncthing-en-ubuntu-antergos-y-rapsberry/)

## Montar disco duro externo

Fuente:

[http://www.mclarenx.com/2015/02/10/raspberry-pi-paso-4-montar-disco-duro-usb/](http://www.mclarenx.com/2015/02/10/raspberry-pi-paso-4-montar-disco-duro-usb/)


## Instalar SAMBA y compartir carpetas

[https://www.redeszone.net/raspberry-pi/como-instalar-un-servidor-samba-en-raspberry-pi-para-compartir-carpetas-en-red/](https://www.redeszone.net/raspberry-pi/como-instalar-un-servidor-samba-en-raspberry-pi-para-compartir-carpetas-en-red/)





_______________

Ya sabéis que podéis encontrarme en:

· Correo electrónico: [educandogeek@gmail.com](mailto:educandogeek@gmail.com)

· Twitter: [@jgurillo](https://twitter.com/jgurillo)

· Suscríbete al Blog: [RSS](http://feeds.feedburner.com/educandogeekblog)

· Suscríbete al Podcast: [RSS](http://feeds.feedburner.com/educandogeek), [Itunes](https://itunes.apple.com/es/podcast/educando-geek/id1110060146?mt=2), [iVoox](https://www.ivoox.com/podcast-educando-geek_sq_f1289274_1.html), [Podkas](http://www.podkas.com/directorio/educando-geek-de-jgurillo)
