Simples comandos productivos
============================

Estos son los comandos productivos más simples que uso en terminales Unix. La mayoría se puede usar en Linux o macOS.

ssh
---

Permite conectarse remotamente a otros equipos por conexión segura/encriptada [SSH](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Secure_Shell) (si tienes router debes habilitar el puerto 22 de tu equipo). La IP\_DESTINO es la IP publica del destino que se puede ver en [What Is My IP](https://web.archive.org/web/20200901184022/https://www.whatismyip.com/) (o terminal: curl icanhazip.com). El destino debe tener un servidor SSH instalado, como [OpenSSH-Server](https://web.archive.org/web/20200901184022/https://help.ubuntu.com/10.04/serverguide/openssh-server.html). Solo pedirá la contraseña del destino:

`ssh usuario@IP_DESTINO`

rsync
-----

Respalda archivos o directorios, monitoreando la transferencia de cada uno de los archivos que está copiando. Si el archivo ya existe y es idéntico entonces no lo reemplaza. (si carpeta termina en carpeta/, entonces respaldará solo el contenido de la carpeta y no la carpeta en si):

`rsync -Pahv carpeta archivo /destino`

También permite transferir archivos a otros equipos por conexión segura:

`rsync -Pahv -e ssh archivo usuario@IP_DESTINO:/directorio_destino`

gpg
---

Encripta archivos con protección de contraseña (creará un nuevo archivo.gpg):

`gpg -c --cipher-algo AES256 archivo` 

 Y desencripta archivos (te pedirá la contraseña del archivo):
 
`gpg archivo.gpg`

lancat
------

Mandar archivos a través de la Red de Área Local ([LAN](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Red_de_%C3%A1rea_local)), fácil y automáticamente. Alguien que mande el archivo (-s):

`lancat -s < archivo` 

Y alguien que reciba el archivo (-r). ([Instalar y usar lancat](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/probando-lancat.html)):

`lancat -r > archivo`

wget
----

Descarga directo un archivo:

`wget www.web.com/archivo` 

O descarga el código [HTML](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/HTML) del sitio y edita con [nano](https://web.archive.org/web/20200901184022/http://es.wikipedia.org/wiki/Nano_(editor_de_texto)):

`wget www.web.com ; nano *.html`

Descarga un sitio completo recursivamente (-r):

`wget -r www.web.com` 

O descarga un sitio aislado con todos sus elementos (-p):

`wget -p www.web.com/sitio-aislado.html`

Descarga todos los enlaces de archivos dentro de un directorio web:

`wget -m -np www.web.com/archivos`

Descarga masivamente archivos con números en secuencia con { }:

`wget www.web.com/archivo{01..50}.jpg`

O con letras:
 
`wget www.web.com/archivo{a..z}.jpg`

curl
----

Bajar archivos con curl:

`curl -O www.web.com/archivo`

O descarga el código HTML de un sitio:

`curl www.web.com > sitio.html`

Descargar masivamente con números en secuencia también se puede con \[ \]:

`curl -O www.web.com/archivo[01-50].jpg`

O incluso con letras:

`curl -O www.web.com/archivo[a-z].jpg`

Recomiendo ver: [curl vs wget](https://web.archive.org/web/20200901184022/http://daniel.haxx.se/docs/curl-vs-wget.html), y la [tabla comparativa](https://web.archive.org/web/20200901184022/http://curl.haxx.se/docs/comparison-table.html) con otras herramientas que descargan archivos.

pastebinit, scrot, recordmydesktop
----------------------------------

Sube archivos de texto directo a [Pastebin](https://web.archive.org/web/20200901184022/http://pastebin.com/) (la URL de descarga aparecerá automáticamente):

`pastebinit -i archivo`

Capturar pantalla en PNG con retardo de 5 segundos (-d):

`scrot -d 5` 

 O seleccionar áreas de la pantalla con puntero (-s):
 
`scrot -s` 

Y capturar ventana en uso con retardo de 5 segundos (-s -b -d):

`scrot -s -b -d 5`

Con recordmydesktop se puede capturar el escritorio con codec de video [Theora](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Theora) (Detener: Ctrl + C):

`recordmydesktop`

foremost
--------

Muy útil para recuperar datos que ya fueron borrados. Puede recuperar [diferentes formatos de imagen, video, o documentos](https://web.archive.org/web/20200901184022/http://manpages.ubuntu.com/manpages/trusty/en/man8/foremost.8.html) (solo coloca el formato que quieres recuperar y la partición):

`sudo foremost -t jpg,mp4 -i /dev/sda1`

dd, mkfs
--------

Lo uso para grabar [imágenes ISO](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Imagen_ISO) al pendrive rápidamente (ve donde se encuentra el dispositvo con lsblk):

`sudo dd if=imagen.iso of=/dev/sdb bs=4M`

Para formatear el pendrive en el [sistema de archivos](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Sistema_de_archivos) [Ext4](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Ext4) (Linux):

`sudo mkfs.ext4 /dev/sdb`

O [NTFS](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/NTFS) (Windows + Compatibilidad con otros):

`sudo mkfs.ntfs /dev/sdb` 

O [FAT32](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Tabla_de_asignaci%C3%B3n_de_archivos#FAT32) que es compatible con Macs:

`sudo mkfs.vfat -F 32 /dev/sdb`

fdisk
-----

Formatear el disco. Con -l lista las particiones existentes.

`sudo fdisk -l`

Para empezar a particionar indica el lugar, por ejemplo /dev/sda, y las letras de uso son borrar partición (d), agregar partición (n), cambiar tipo de partición (t), listar tipos de partición soportados (l), escribir los cambias hechos (w), y salir de fdisk (q):

`sudo fdisk /dev/sda`

ffmpeg, lame, mediainfo
-----------------------

[FFmpeg](https://web.archive.org/web/20200901184022/http://ffmpeg.org/) encodea cualquier tipo de video/audio ([guía extensa](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/encodear-con-ffmpeg.html)):

`ffmpeg -i entrada.mkv -c:v libx264 -crf 18 -c:a flac salida.mkv` 

 O capturar video streaming:
 
`ffmpeg -i http://url-streaming -c:v copy -c:a copy video.mkv`

Grabar el escritorio en video de alta calidad (salir: Q):

`ffmpeg -f x11grab -s 1440x900 -framerate 30 -i :0.0 -c:v libx264 -qp 0 -preset ultrafast salida.mkv`

Grabar audio desde el micrófono del notebook:

`ffmpeg -f alsa -i pulse salida.wav` 

O grabar video+audio desde la cámara del notebook (salir: Ctrl + C). Vean en alsamixer si tienen el micrófono en captura al 100 (Cambiar a captura alsamixer: TAB):

`ffmpeg -f video4linux2 -i /dev/video0 -f alsa -i pulse salida.mkv`

Encodea cualquier audio a MP3 con [VBR](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Tasa_de_bits_variable) de alta calidad ([guía extensa de encodear audio](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2009/encodear-audio-en-linux.html)):

`lame audio.wav -V 0 audio.mp3`

Para ver toda la información de un archivo de medios imagen/video/audio:

`mediainfo video.mkv`

youtube-dl, cclive, mpv
-----------------------

Descargar videos de Youtube/Vimeo/Dailymotion con [youtube-dl](https://web.archive.org/web/20200901184022/http://rg3.github.io/youtube-dl/) (instala python-pip, y luego: sudo pip install youtube\_dl):

`youtube-dl http://youtube.com/asdf` 

O con cclive (solo Youtube):

`cclive http://youtube.com/asdf`

Y ver videos desde Youtube/Vimeo/Dailymotion:

`mpv http://youtube.com/asdf` 

O video y audio en web con el reproductor [mpv](https://web.archive.org/web/20200901184022/http://mpv.io/) ([porqué usar mpv](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/mpv-el-sucesor-de-mplayer2.html)):

`mpv http://web.com/video.mp4` 

También si quisiéramos escuchar solo la música de un video:

`mpv --no-video http://youtube.com/asdf`

Descargar video en linea con mpv:

`mpv --stream-dump=video.mkv http://web.com/video-en-linea` 

O ver la cámara del notebook:

`mpv tv://`

mkvextract, mkvmerge
--------------------

Para extraer las pistas de video, audio, subtitulo de un MKV (incluido con [mkvtoolnix](https://web.archive.org/web/20200901184022/https://www.bunkus.org/videotools/mkvtoolnix/), para ver número de pista: mkvmerge -i video.mkv):

`mkvextract tracks video-audio.mkv 0:video-solo.mkv 1:audio.dts` 

Y volver a unir con mkvmerge:

`mkvmerge video-solo.mkv audio.dts -o unido.mkv`

feh, convert
------------

Ver imagen en web:

`feh http://web.com/imagen.jpg` 

Ver varias imágenes secuenciales en web (cambiar imagen: flechas derecha/izquierda. Pantalla completa: V):
 
`feh http://web.com/imagen{01..50}.jpg` 

O abrir todas las imágenes del directorio actual con la imagen ajustada a la pantalla (-.):

`feh -.`

Redimensiona el ancho de una imagen respetando la relación de aspecto (convert viene incluido con [imagemagick](https://web.archive.org/web/20200901184022/http://www.imagemagick.org/)):

`convert -sample 640x imagen.jpg nueva.jpg`

ctorrent, aria2c, transmission-cli, peerflix
--------------------------------------------

Descargar torrents:

`ctorrent archivo.torrent`

O enlaces magnéticos de manera rápida (salir: Ctrl + C):

`aria2c "magnet:enlace"`

Si quisieran limitar velocidades de descarga (-d) o subida (-u) en KB/s:

`transmission-cli -d 800 -u 30 archivo.torrent`

Para video streaming de torrents ([instalar y usar Peerflix](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/probando-peerflix.html)):

`peerflix archivo.torrent --mpv`

touch, mkdir, file
------------------

Para crear varios archivos a la vez:

`touch archivo01.txt archivo02.txt` 

`touch archivo{01..10}.txt` 

`touch archivo{01,02,03}.txt`

Y crear varias carpetas:

`mkdir carpeta01 carpeta02` 

`mkdir carpeta{01..10}`

Ver descripción de todos los tipos de archivos en un directorio:

`file *`

7z, zip, unzip
--------------

Para comprimir:

`7z a comprimir.rar archivos` 

Y descomprimir cualquier compresor de archivo:

`7z x descomprimir.rar`

Y si solo usas [Zip](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Formato_de_compresi%C3%B3n_ZIP):

`zip comprimir.zip archivos` 

Descomprimir Zip:

`unzip descomprimir.zip`

grep
----

Localiza palabra dentro de un archivo:

`grep palabra archivo` 

O localizar frases dentro de un archivo:

`grep 'frase larga' archivo` 

También localizar palabra al interior de todos los archivos del actual directorio:

`grep palabra *`

Localiza dos o más palabras dentro de un archivo (-e):

`grep -e palabra1 -e palabra2 archivo` 

También buscar palabras incluidas con mayúsculas (-i):

`grep -i palabra archivo` 

O mostrar las filas de texto bajo palabra, por ejemplo 5 filas (-A):

`grep palabra -A 5 archivo` 

O mostrar las 3 filas arriba de palabra (-B):

`grep palabra -B 3 archivo`

Localiza recursivamente palabra en carpeta con archivos (-r):

`grep -r palabra /carpeta` 

O localiza palabra de otro comando:

`history | grep palabra`

Mostrar solamente la URL de todas las imágenes JPG de un archivo fuente u HTML:

`grep -o -i 'https:[^>]*.jpg' archivo.html`

sed
---

Reemplazar palabra o carácter en un archivo de texto, y el resultado en archivo2:

`sed 's/vieja/nueva/g' archivo > archivo2` 

O reemplazar varias palabras a la vez:

`sed 's/vieja/nueva/g ; s/vieja2/nueva2/g' archivo > archivo2`

Si el texto tuviera barras diagonales "/", se pueden usar barras verticales o diagonales invertidas "| \\" como reemplazo, por ejemplo para borrar todas las cursivas "<i> y </i>" dentro de un subtitulo:

`sed 's|<i>||g ; s|</i>||g' sub.srt > sub2.srt` 

Y usando diagonales invertidas:

`sed 's\vieja\nueva\g' archivo > archivo2`

Útil para eliminar lineas, por ejemplo borrar las 4 primeras lineas (1,4d):

`sed '1,4d' archivo > archivo2` 

Borrar las lineas que contengan palabra (/d):

`sed '/palabra/d' archivo > archivo2` 

O dejar las lineas que contengan palabra (/!d):

`sed '/palabra/!d' archivo > archivo2` 

Y borrar la última linea ($d):

`sed '$d' archivo > archivo2`

O también mostrar una linea completa junto con cat, por ejemplo la 4ta linea (-n 4p):

`cat archivo | sed -n '4p'` 

Mostrar lineas por separado, lineas 2 y 6 (2p ; 6p):

`sed -n '2p ; 6p' archivo > archivo 2` 

Si quisiéramos cambiar palabra solo en la 3ra linea (3s):

`sed '3s/vieja/nueva/g' archivo > archivo2` 

También agregar una linea en la 5ta linea y empujar las demás hacia abajo (5i):

`sed '5i\Linea agregada' archivo > archivo2` 

O reemplazar todo el texto de la 6ta linea (6c):

`sed '6c\Linea reemplazada' archivo > archivo2` 

Y agregar una nueva linea después la 7ma linea, creando una nueva 8va linea (7a):

`sed '7a\Linea agregada después' archivo > archivo2`

Para sobreescribir el mismo archivo sin crear otro archivo usen -i:

`sed -i '1d' archivo` 

Y si quieren sumar diferentes ordenes usen -e:
 
`sed -e '1c\Linea reemplazada' -e '2i\Linea agregada' archivo > archivo2`

Pegar la 1ra linea con la 2da linea, y así consecutivamente en par, la 3ra con la 4ta, la 5ta con la 6ta, etc:

`sed 'N;s/\n/ /' archivo > archivo2` 

Agregar palabra al inicio de cada linea (s/^):

`sed 's/^/palabra/' archivo > archivo2` 

O agregar palabra al final de cada linea (s/$):

`sed 's/$/palabra/' archivo > archivo2` 

 Agregar una linea al final, la cola del archivo ($a):
 
`sed '$a\Linea al final' archivo > archivo2` 

 Y dar saltos de linea (creando una nueva linea) cada vez que se tope con el carácter de doble comillas " (también puede ser otro carácter):
 
`sed 's/"/\n/g' archivo > archivo2`

cut
---

Para seleccionar cantidad de caracteres a mostrar, por ejemplo que muestre solo desde el carácter 5 al 10 en todas las lineas del archivo (5-10):

`cut -c 5-10 archivo` 

También que muestre desde el carácter 5 en adelante en cada línea (5-):

`cut -c 5- archivo` 

Que muestre solo los primeros 3 caracteres (-3):

`cut -c -3 archivo` 

O sumar dos sentencias, la primera hasta el carácter 5 y la segunda desde el carácter 20 (-5,20-):

`cut -c -5,20-`

Es útil usando grep si hay demasiado texto y solo queremos pocas lineas:

`grep palabra archivo | cut -c 5-10`

Se pueden usar delimitadores, por ejemplo hasta la coma ',' (también se pueden otros / | # @, etc). Mostrar solo la 4ta oración después de la coma (-f 4):

`cut -d ',' -f 4 archivo` 

O mostrar solo la 4ta y 6ta oración después de la coma (-f 4,6):

`cut -d ',' -f 4,6 archivo` 

O mostrar la 4ta oración e incluir todo lo que aparezca entre medio con la 6ta oración (-f 4-6):

`cut -d ',' -f 4-6 archivo`

head, tail
----------

Con head se pueden ver las primeras lineas de un texto, digamos las 3 primeras lineas (-n 3):

`head -n 3 archivo` 

Con tail se pueden ver las últimas lineas, digamos las 2 últimas lineas (-n 2):

`tail -n 2 archivo` 

O simplemente mostrar las últimas lineas (10 por defecto) de otro comando:

`history | tail`

find, locate
------------

Encuentra archivos y carpetas en cualquier directorio recursivamente (/ruta -name):

`find /ruta -name palabra` 

O buscar un tipo de archivo determinado en el directorio actual recursivamente (. -name):

`find . -name *.jpg`

Busca archivos por el sistema mostrando todas sus rutas:

`locate palabra`

nano, echo, cat, alias
----------------------

El editor de texto fácil y entendible, solo para crear un archivo y ponerse a escribir (Guardar: Ctrl + O. Salir: Ctrl + X):

`nano archivo` 

O lee y edita el código HTML de un sitio:
 
`` nano *.html `wget www.web.com` ``

Para crear y agregar más texto a una nota/archivo (para reemplazar todo lo escrito solo usa una flecha: >):

`echo "Texto" >> notas` 

Y cat para mostrar texto de archivos directo en la terminal:

`cat archivo` 

O también enumerar las lineas de un texto (-n):

`cat -n archivo`

Útil para dar un nombre corto a comandos muy largos, y ser usado después (pueden guardar manualmente sus alias creando el archivo ~/.bash\_aliases

`alias comando="comandos con ordenes muy largas"`

iconv
-----

Permite cambiar la [codificación de caracteres](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Codificaci%C3%B3n_de_caracteres) de un archivo de texto, por ejemplo cambiar un subtitulo [UTF-8](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/UTF-8) a un [ISO-8859-15](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/ISO_8859-15) para compatibilidad occidental de caracteres en español:

`iconv -f UTF-8 -t ISO-8859-15 sub1.srt > sub2.srt`

rm, trash-cli
-------------

Para eliminar definitivamente varios archivos que terminen o empiecen con la misma palabra:

`rm *rchivo archiv*` 

O borrar todos los archivos en el directorio actual (sin tocar las carpetas):

`rm *` 

O solo con extensiones especificas:

`rm *.jpg`

Para eliminar una carpeta se debe hacer recursivamente (-r). También eliminar todas las carpetas y archivos sueltos sin indicar nombres en el directorio actual (-r \*):

`rm -r carpeta` `rm -r *`

Mandar archivos a la papelera (trash):

`trash archivo` 

Ver lo que hay en la papelera (trash-list):

`trash-list` 

Y eliminar definitivamente lo que hay en la papelera (trash-empty):
 
`trash-empty`

cp, gcp
-------

Copia archivos rápidamente dentro del sistema o otros dispositivos ([cp es más rápido que rsync](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/respaldando-rsync-cp-pv.html), pero sin información de transferencias y copia archivos aunque existan en destino):

`cp archivo /destino` 

También copia recursivamente carpetas (-r):

`cp -r carpeta /destino` 

Y copiar todo el contenido del actual directorio:

`cp -r * /destino`

Acá tenemos a gcp que se comporta igual que cp, pero con información de transferencias:

`gcp archivo /destino` 

Y copia recursivamente:

`gcp -r carpeta /destino`

pv, bar
-------

Con pv y bar se puede ver información de transferencia (aunque no están hechos para copiar, se usa casi igual), pero hay que poner el nombre del destinatario, no solo la ruta:

`pv archivo > /destino/archivo` 

`bar archivo > /destino/archivo`

mv, mmv
-------

Para renombrar un archivo:

`mv viejo nuevo` 

O mover archivos de lugar:

`mv origen /destino`

Renombrar archivos masivamente (conservando extensión):

`mmv "viejos*" "nuevos#1"` 

Renombrar extensión masivamente (de .jpg a .png):

`mmv "*.jpg" "#1.png"` 

Poner extensión a archivos sin extensión (a .txt):

`mmv "archivos*" "archivos#1.txt"`

pycp, pymv
----------

Lo mismo que cp (aunque [es más lento que cp](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/respaldando-rsync-cp-pv.html)):

`pycp archivo /destino` 

Y pymv, pero con una barra de progreso e información de transferencia (instala python-pip, y luego: sudo pip install pycp):

`pymv archivo /destino`

Si están transfiriendo una carpeta con muchos archivos usen -g para que aparezca una sola barra y no múltiples (no necesita opción de recursiva):

`pycp -g carpeta /destino`

cd
--

Con cd se pueden escalar directorios:

`cd directorio` 

 También ir a uno nuevo, como raíz (/):
 
`cd /` 

O ir al home (~), también se vuelve al home simplemente escribiendo solo cd:

`cd ~` 

Y retroceder un nivel:

`cd ..`

ls, wc
------

Para ver el tamaño de los archivos (-sh):

`ls -sh` 

Ver los permisos/dueños (-l):

`ls -l` 

Y ver todos los archivos ocultos (-a) (se pueden combinar):

`ls -a`

Localizar archivo que comience con una palabra:

`ls archiv*` 

O mostrar solo con extensión .jpg:

`ls *.jpg` 

También que muestre solo con algunas extensiones (\*.{jpg,gif,png}):

`ls *.{jpg,gif,png}`

Combinando ls + wc se puede contar la cantidad de archivos y carpetas de un directorio:

`ls | wc -l` 

Y que también sume los archivos ocultos (-A) recursivamente en las demás carpetas (-R):

`ls -AR | wc -l`

Listar y usar grep para mostrar solo los archivos que usen esa palabra:

`ls | grep palabra` 

Y recursivamente (-R):

`ls -R | grep *.jpg`

du
--

Con du se puede ver el peso de todos los directorios de una carpeta (-sh \*):

`du -sh *` 

O el peso total del directorio actual (-sh):

`du -sh`

Con sort se puede listar el peso de menor a mayor (al revés: -hr):

`du -sh * | sort -h` 

O ver el peso que ocupa de cada app en el disco en macOS:

`du -sh /Applications/*`

ncdu
----

Muy parecido a du pero navegable a través de los directorios:

`ncdu`

tree
----

Permite ver el árbol de los directorios que se encuentran dentro:

`tree -d directorio` 

Y mostrar un tipo de archivo predeterminado (-P):

`tree -P *.jpg directorio`

chmod, chown
------------

Modificar permisos de un archivo (u: usuario, g: grupo, o: otros, a: todos, r: leer, w: escribir, x: ejecutar), con signo "+" sumas permisos, con signo "-" quitas permisos ([guía extensa](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2009/permisos-de-usuario-en-linux.html)):

`chmod ugoa+rwx archivo` 

Y cambiar al dueño de un archivo (chown):

`chown usuario:usuario archivo`

apt
---

El poderoso APT que desde la [versión 1.0](https://web.archive.org/web/20200901184022/https://mvogt.wordpress.com/2014/04/04/apt-1-0/) puede usar también 'apt orden'. Para sistemas basados en Debian, como [Ubuntu](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/el-futuro-unificado-de-ubuntu.html) 14.04 LTS y [elementary OS Freya](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2014/probando-elementary-os-freya-beta.html). Para actualizar la lista de software (update):

`sudo apt update` 

Y actualizar sistema (upgrade):

`sudo apt upgrade`

Instalar software (install):

`sudo apt install nombre` 

Y remover software (remove):
 
`sudo apt remove nombre`

Buscar software (search):

`apt search nombre` 

Y ver información de un paquete/app (show):

`apt show nombre`

brew
----

[Homebrew es usado solo en macOS](https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/os-x-y-homebrew.html). Puedes instalar, remover y mantener actualizadas tus apps CLI:

`brew install nombre` 

Y apps de interfaz que encuentres en sus repositorios:

`brew-cask install nombre (apps gráficas)`

Y mantener actualizado:

`brew update` 

`brew upgrade`

open
----

En macOS puedes abrir un archivo con open y lo abrirá con su app predeterminada:

`open archivo`

nmap, arp-scan
--------------

Para ver a todos los que están conectados a tu Red de Área Local (LAN), incluidos los con Wi-Fi (aparece la IP, MAC y el fabricante):

`sudo nmap -sP 192.168.1.0/24`

Con arp-scan se puede automatizar el proceso, mostrará las IPs y dirección de hardware de todos los demás conectados a la Red de Área Local:

`sudo arp-scan -l` 

Y si estás en un notebook usa el Wi-Fi (wlan0):

`sudo arp-scan -l -I wlan0`

nmcli, iwlist
-------------

Ver la lista de señales Wi-Fi cercanas:

`nmcli -p dev wifi list`

Para ver las señales Wi-Fi cercanas con información detallada:

`sudo iwlist wlan0 scan`

ifconfig, iwconfig, wavemon
---------------------------

Para ver cuantos datos has descargado (RX) y subido (TX) a Internet desde que iniciaste la sesión actual:

`ifconfig eth0 | grep Bytes` 

Por Ethernet (eth0) y Wi-Fi (wlan0):

`ifconfig wlan0 | grep Bytes`

Para ver la calidad de señal Wi-Fi actual (70 máx), y el nivel de señal [dBm](https://web.archive.org/web/20200901184022/http://es.wikipedia.org/wiki/DBm) (prueben acercándose y alejándose para ver como afecta):

`iwconfig wlan0 | grep Quality`

Con wavemon se puede monitorear la intensidad de la señal Wi-Fi y otros datos en pantalla completa:

`wavemon`

htop, iotop, pydf
-----------------

Con htop se puede monitorear el uso de procesos que están corriendo, también uso de [CPU](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento), [RAM](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio) y [Swap](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Espacio_de_intercambio) (los que utilizan más procesamiento aparecen en la cabecera):

`htop` 

Y con iotop puedes ver que procesos están escribiendo y leyendo en tu disco:

`sudo iotop`

Muy practico para estar al tanto de cuanto espacio estás ocupando o te queda en tus discos duros, particiones, pendrives o discos duros móviles:

`pydf`

lm-sensors, hddtemp, acpi
-------------------------

Para ver la temperatura del procesador (Core son las CPU) (luego de instalar: sudo sensors-detect ; sudo service kmod start):

`sensors` 

Con hddtemp se monitorea la temperatura del disco duro:

`sudo hddtemp /dev/sda`

Y para monitorear cuanta batería queda o se está cargando en el notebook:

`acpi -i`

netstat, free, ps
-----------------

Ver los puertos abiertos (escuchando) que está ocupando cada app:

`sudo netstat -plunt`

Ver la RAM real en uso y que está libre:

`free -h | grep -e usado -e cache`

Con ps se puede ver la lista de todos los procesos que están corriendo y el usuario que los usa:

`ps aux` 

O buscar el nombre de un proceso corriendo:

`ps x | grep -i nombreapp`

Para información en un-solo-lugar de uso de cpu, ram, swap, red, procesos, instala [Glances](https://web.archive.org/web/20200901184022/http://askubuntu.com/a/293447).

lsblk, mount, umount
--------------------

Parecido a pydf, pero muestra la jerarquía de las particiones, y puede ver los dispositivos conectados aunque no estén montados:

`lsblk`

Con mount se puede montar el dispositivo (pendrive, disco duro portátil) al ver donde está con lsblk:

`sudo mount /dev/sdb1 /media/usuario/` 

Y con umount se puede desmontar para desconectar:

`sudo umount /media/usuario/`

lspci, lshw
-----------

Para ver el tipo de [GPU](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Unidad_de_procesamiento_gr%C3%A1fico) (gráficos) que usa el equipo, y fabricante del modelo Wi-Fi:

`lspci | grep -e VGA -e Wireless`

Ver cada parte de todo el hardware, su fabricante y modelos en detalle:

`sudo lshw` 

También ver solo información del procesador:

`sudo lshw | grep CPU -A 12`

speedometer, speedtest-cli
--------------------------

Para monitorear la velocidad en la conexión, en descarga (-r):

`speedometer -r eth0` 

Y subida (-t), en un gráfico (Wi-Fi: wlan0):

`speedometer -t eth0`

Con [speedtest-cli](https://web.archive.org/web/20200901184022/https://github.com/sivel/speedtest-cli) se realizan test de velocidad de descarga y subida (instala python-pip, y luego: sudo pip install speedtest-cli):

`speedtest-cli`

ping
----

Ver si hay perdida de paquetes en una conexión inestable, y cuanto se demoran los paquetes en milisegundos para ir y volver (salir: Ctrl + C):

`ping www.google.com` 

O transmitir una cantidad de paquetes predeterminada (-c):

`ping -c 5 www.google.com`

whoami, who, pwd
----------------

Con whoami se puede ver el nombre del usuario actual:

`whoami` 

Con who se ven los todos los usuarios conectados:

`who` 

Y pwd muestra la ruta completa del directorio actual:

`pwd`

tcpdump, whois, host
--------------------

Para monitorear todo lo que pasa por el puerto 80 [TCP](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Transmission_Control_Protocol) (usado en [HTTP](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Hypertext_Transfer_Protocol)) (Salir: Ctrl + C):

`sudo tcpdump tcp port 80`

Para ver información de dueño del dominio, servidores, y creación del dominio:

`whois web.com` 

Y host puede ver la [IP](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Direcci%C3%B3n_IP) del dominio:

`host web.com`

traceroute, dig
---------------

Muestra la ruta de viaje de un dominio a través de servidores:

`traceroute google.cl` 

Ve información de un domino DNS: 

`dig google.cl`

tshark
------

O mejor conocido como [Wireshark](https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Wireshark). Sirve para monitorear el tráfico de conexiones. Primero hay que ver el nombre de las interfaces disponibles (-D):

`sudo tshark -D` 

Y luego monitorear esa conexión con su nombre (-i):

`sudo tshark -i en0`

sleep, notify-send, date
------------------------

Ejecutar una orden en el tiempo dado (sleep), además con notificación (notify-send), hora (date), y música de fondo (mpv). Como un despertador:

`sleep 1h 30m 10s ; notify-send -u critical ¡Despierta! "$(date)" ; mpv audio.mp3`

watch, alsamixer
----------------

Refresca un comando cada 2 segundos para observar cambios (1 segundo: -n 1). Por ejemplo si estuviéramos monitoreando el peso de los archivos que se están transfiriendo o bajando:

`watch ls -sh`

Con alsamixer se pueden controlar los niveles de audio de los altavoces, micrófono en captura (para cambiar a captura: TAB), y las entradas de audio en linea:

`alsamixer`

xkill, killall, kill
--------------------

Las tres formas de matar o cerrar a la fuerza apps/procesos. Con xkill se apunta con el cursor a la ventana y la mata:

`xkill` 

Con killall hay que escribir el nombre de la app:

`killall nombre` 

Con kill se escribe el PID de la app, que se obtiene con "ps x | grep -i nombreapp":

`kill pidapp`

Pueden seguir viendo [algunas recomendaciones en Reddit](https://web.archive.org/web/20200901184022/http://www.reddit.com/r/linux/comments/eizx9/top_linux_commands_every_linux_user_should_know/) y visitar [/r/commandline](https://web.archive.org/web/20200901184022/http://www.reddit.com/r/commandline), ver un [indice de comandos](https://web.archive.org/web/20200901184022/http://ss64.com/bash/) útiles, leer [sus manuales](https://web.archive.org/web/20200901184022/http://www.die.net/) o de [otros manuales de Ubuntu](https://web.archive.org/web/20200901184022/http://manpages.ubuntu.com/), o ir [aprendiendo más detalladamente](https://web.archive.org/web/20200901184022/http://linuxcommand.org/lc3_learning_the_shell.php). También pueden empezar creando [shell scripts básicos](https://web.archive.org/web/20200901184022/http://cont3mpo.blogspot.com/2009/09/interpretar-ordenes-shell-script.html) y ver comandos más complejos en [Commandlinefu](https://web.archive.org/web/20200901184022/http://www.commandlinefu.com/). O leer en linea el libro [Conquering the Command Line](https://web.archive.org/web/20200901184022/http://conqueringthecommandline.com/book). También una [Introducción a Unix](https://web.archive.org/web/20200901184022/http://www.oliverelliott.org/article/computing/tut_unix/), y [100 comandos útiles](https://web.archive.org/web/20200901184022/http://www.oliverelliott.org/article/computing/ref_unix/).

25 de octubre, 2014
