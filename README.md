<article>
      <h1>Simples comandos productivos</h1>

      <p>Estos son los comandos productivos más simples que uso en terminales Unix. La mayoría se puede usar en Linux o macOS.</p>

      <h2>ssh</h2>

      <p>Permite conectarse remotamente a otros equipos por conexión segura/encriptada <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Secure_Shell"><abbr title="Secure Shell">SSH</abbr></a> (si tienes router debes habilitar el puerto 22 de tu equipo). La IP_DESTINO es la <abbr title="Internet Protocol">IP</abbr> publica del destino que se puede ver en <a href="https://web.archive.org/web/20200901184022/https://www.whatismyip.com/">What Is My IP</a> (o terminal: curl icanhazip.com). El destino debe tener un servidor <abbr title="Secure Shell">SSH</abbr> instalado, como <a href="https://web.archive.org/web/20200901184022/https://help.ubuntu.com/10.04/serverguide/openssh-server.html">OpenSSH-Server</a>. Solo pedirá la contraseña del destino:</p>

      <code>ssh usuario@IP_DESTINO</code>

      <h2>rsync</h2>

      <p>Respalda archivos o directorios, monitoreando la transferencia de cada uno de los archivos que está copiando. Si el archivo ya existe y es idéntico entonces no lo reemplaza. (si carpeta termina en carpeta/, entonces respaldará solo el contenido de la carpeta y no la carpeta en si):</p>

      <code>rsync -Pahv carpeta archivo /destino</code>

      <p>También permite transferir archivos a otros equipos por conexión segura:</p>

      <code>rsync -Pahv -e ssh archivo usuario@IP_DESTINO:/directorio_destino</code>

      <h2>gpg</h2>

      <p>Encripta archivos con protección de contraseña (creará un nuevo archivo.gpg). Y desencripta archivos (te pedirá la contraseña del archivo):</p>

      <code>gpg -c --cipher-algo AES256 archivo</code>

      <code>gpg archivo.gpg</code>

      <h2>lancat</h2>

      <p>Mandar archivos a través de la Red de Área Local (<a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Red_de_%C3%A1rea_local"><abbr title="Local Area Network">LAN</abbr></a>), fácil y automáticamente. Alguien que mande el archivo (-s). Y alguien que reciba el archivo (-r). (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/probando-lancat.html">Instalar y usar lancat</a>):</p>

      <code>lancat -s &lt; archivo</code>

      <code>lancat -r &gt; archivo</code>

      <h2>wget</h2>

      <p>Descarga directo un archivo. O descarga el código <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/HTML"><abbr title="HyperText Markup Language">HTML</abbr></a> del sitio y edita con <a href="https://web.archive.org/web/20200901184022/http://es.wikipedia.org/wiki/Nano_(editor_de_texto)">nano</a>:</p>

      <code>wget www.web.com/archivo</code>

      <code>wget www.web.com ; nano *.html</code>

      <p>Descarga un sitio completo recursivamente (-r). O descarga un sitio aislado con todos sus elementos (-p):</p>

      <code>wget -r www.web.com</code>

      <code>wget -p www.web.com/sitio-aislado.html</code>

      <p>Descarga todos los enlaces de archivos dentro de un directorio web:</p>

      <code>wget -m -np www.web.com/archivos</code>

      <p>Descarga masivamente archivos con números en secuencia con { }, o con letras:</p>

      <code>wget www.web.com/archivo{01..50}.jpg</code>

      <code>wget www.web.com/archivo{a..z}.jpg</code>

      <h2>curl</h2>

      <p>Se puede subir cualquier tipo de archivo a <a href="https://web.archive.org/web/20200901184022/https://transfer.sh/">transfer.sh</a>, un sitio que almacena por 2 semanas archivos de hasta 5GB (la <abbr title="Uniform Resource Locator">URL</abbr> de descarga aparecerá automáticamente):</p>

      <code>curl -T archivo https://transfer.sh</code>

      <p>Bajar archivos con curl. O descarga el código <abbr title="HyperText Markup Language">HTML</abbr> de un sitio:</p>

      <code>curl -O www.web.com/archivo</code>

      <code>curl www.web.com &gt; sitio.html</code>

      <p>Descargar masivamente con números en secuencia también se puede con [ ], incluso con letras:</p>

      <code>curl -O www.web.com/archivo[01-50].jpg</code>

      <code>curl -O www.web.com/archivo[a-z].jpg</code>

      <p>Recomiendo ver: <a href="https://web.archive.org/web/20200901184022/http://daniel.haxx.se/docs/curl-vs-wget.html">curl vs wget</a>, y la <a href="https://web.archive.org/web/20200901184022/http://curl.haxx.se/docs/comparison-table.html">tabla comparativa</a> con otras herramientas que descargan archivos.</p>

      <h2>pastebinit, scrot, recordmydesktop</h2>

      <p>Sube archivos de texto directo a <a href="https://web.archive.org/web/20200901184022/http://pastebin.com/">Pastebin</a> (la URL de descarga aparecerá automáticamente):</p>

      <code>pastebinit -i archivo</code>

      <p>Capturar pantalla en <abbr title="Portable Network Graphics">PNG</abbr> con retardo de 5 segundos (-d). O seleccionar áreas de la pantalla con puntero (-s). Y capturar ventana en uso con retardo de 5 segundos (-s -b -d):</p>

      <code>scrot -d 5</code>

      <code>scrot -s</code>

      <code>scrot -s -b -d 5</code>

      <p>Con recordmydesktop se puede capturar el escritorio con codec de video <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Theora">Theora</a> (Detener: Ctrl + C):</p>

      <code>recordmydesktop</code>

      <h2>foremost</h2>

      <p>Muy útil para recuperar datos que ya fueron borrados. Puede recuperar <a href="https://web.archive.org/web/20200901184022/http://manpages.ubuntu.com/manpages/trusty/en/man8/foremost.8.html">diferentes formatos de imagen, video, o documentos</a> (solo coloca el formato que quieres recuperar y la partición):</p>

      <code>sudo foremost -t jpg,mp4 -i /dev/sda1</code>

      <h2>dd, mkfs</h2>

      <p>Lo uso para grabar <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Imagen_ISO">imágenes ISO</a> al pendrive rápidamente (ve donde se encuentra el dispositvo con lsblk):</p>

      <code>sudo dd if=imagen.iso of=/dev/sdb bs=4M</code>

      <p>Para formatear el pendrive en el <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Sistema_de_archivos">sistema de archivos</a> <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Ext4">Ext4</a> (Linux), o <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/NTFS">NTFS</a> (Windows + Compatibilidad con otros), o <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Tabla_de_asignaci%C3%B3n_de_archivos#FAT32">FAT32</a> que es compatible con Macs:</p>

      <code>sudo mkfs.ext4 /dev/sdb</code>

      <code>sudo mkfs.ntfs /dev/sdb</code>

      <code>sudo mkfs.vfat -F 32 /dev/sdb</code>

      <h2>fdisk</h2>

      <p>Formatear el disco. Con -l lista las particiones existentes.</p>

      <code>sudo fdisk -l</code>

      <p>Para empezar a particionar indica el lugar, por ejemplo /dev/sda, y las letras de uso son borrar partición (d), agregar partición (n), cambiar tipo de partición (t), listar tipos de partición soportados (l), escribir los cambias hechos (w), y salir de fdisk (q):</p>

      <code>sudo fdisk /dev/sda</code>

      <h2>ffmpeg, lame, mediainfo</h2>

      <p><a href="https://web.archive.org/web/20200901184022/http://ffmpeg.org/">FFmpeg</a> encodea cualquier tipo de video/audio (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/encodear-con-ffmpeg.html">guía extensa</a>). O capturar video streaming:</p>

      <code>ffmpeg -i entrada.mkv -c:v libx264 -crf 18 -c:a flac salida.mkv</code>

      <code>ffmpeg -i http://url-streaming -c:v copy -c:a copy video.mkv</code>

      <p>Grabar el escritorio en video de alta calidad (salir: Q):</p>

      <code>ffmpeg -f x11grab -s 1440x900 -framerate 30 -i :0.0 -c:v libx264 -qp 0 -preset ultrafast salida.mkv</code>

      <p>Grabar audio desde el micrófono del notebook. O grabar video+audio desde la cámara del notebook (salir: Ctrl + C). Vean en alsamixer si tienen el micrófono en captura al 100 (Cambiar a captura alsamixer: TAB):</p>

      <code>ffmpeg -f alsa -i pulse salida.wav</code>

      <code>ffmpeg -f video4linux2 -i /dev/video0 -f alsa -i pulse salida.mkv</code>

      <p>Encodea cualquier audio a MP3 con <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Tasa_de_bits_variable"><abbr title="Variable Bitrate">VBR</abbr></a> de alta calidad (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2009/encodear-audio-en-linux.html">guía extensa de encodear audio</a>):</p>

      <code>lame audio.wav -V 0 audio.mp3</code>

      <p>Para ver toda la información de un archivo de medios imagen/video/audio:</p>

      <code>mediainfo video.mkv</code>

      <h2>youtube-dl, cclive, mpv</h2>

      <p>Descargar videos de Youtube/Vimeo/Dailymotion con <a href="https://web.archive.org/web/20200901184022/http://rg3.github.io/youtube-dl/">youtube-dl</a> (instala python-pip, y luego: sudo pip install youtube_dl). O con cclive (solo Youtube):</p>

      <code>youtube-dl http://youtube.com/asdf</code>

      <code>cclive http://youtube.com/asdf</code>

      <p>Y ver videos desde Youtube/Vimeo/Dailymotion. O video y audio en web con el reproductor <a href="https://web.archive.org/web/20200901184022/http://mpv.io/">mpv</a> (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/mpv-el-sucesor-de-mplayer2.html">porqué usar mpv</a>). También si quisiéramos escuchar solo la música de un video:</p>

      <code>mpv http://youtube.com/asdf</code>

      <code>mpv http://web.com/video.mp4</code>

      <code>mpv --no-video http://youtube.com/asdf</code>

      <p>Descargar video en linea con mpv. O ver la cámara del notebook:</p>

      <code>mpv --stream-dump=video.mkv http://web.com/video-en-linea</code>

      <code>mpv tv://</code>

      <h2>mkvextract, mkvmerge</h2>

      <p>Para extraer las pistas de video, audio, subtitulo de un MKV (incluido con <a href="https://web.archive.org/web/20200901184022/https://www.bunkus.org/videotools/mkvtoolnix/">mkvtoolnix</a>, para ver número de pista: mkvmerge -i video.mkv). Y volver a unir con mkvmerge:</p>

      <code>mkvextract tracks video-audio.mkv 0:video-solo.mkv 1:audio.dts</code>

      <code>mkvmerge video-solo.mkv audio.dts -o unido.mkv</code>

      <h2>feh, convert</h2>

      <p>Ver imagen en web. Ver varias imágenes secuenciales en web (cambiar imagen: flechas derecha/izquierda. Pantalla completa: V). O abrir todas las imágenes del directorio actual con la imagen ajustada a la pantalla (-.):</p>

      <code>feh http://web.com/imagen.jpg</code>

      <code>feh http://web.com/imagen{01..50}.jpg</code>

      <code>feh -.</code>

      <p>Redimensiona el ancho de una imagen respetando la relación de aspecto (convert viene incluido con <a href="https://web.archive.org/web/20200901184022/http://www.imagemagick.org/">imagemagick</a>):</p>

      <code>convert -sample 640x imagen.jpg nueva.jpg</code>

      <h2>ctorrent, aria2c, transmission-cli, peerflix</h2>

      <p>Descargar torrents o enlaces magnéticos de manera rápida (salir: Ctrl + C):</p>

      <code>ctorrent archivo.torrent</code>

      <code>aria2c "magnet:enlace"</code>

      <p>Si quisieran limitar velocidades de descarga (-d) o subida (-u) en KB/s:</p>

      <code>transmission-cli -d 800 -u 30 archivo.torrent</code>

      <p>Para video streaming de torrents (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/probando-peerflix.html">instalar y usar Peerflix</a>):</p>

      <code>peerflix archivo.torrent --mpv</code>

      <h2>touch, mkdir, file</h2>

      <p>Para crear varios archivos a la vez:</p>

      <code>touch archivo01.txt archivo02.txt</code>

      <code>touch archivo{01..10}.txt</code>

      <code>touch archivo{01,02,03}.txt</code>

      <p>Y crear varias carpetas:</p>

      <code>mkdir carpeta01 carpeta02</code>

      <code>mkdir carpeta{01..10}</code>

      <p>Ver descripción de todos los tipos de archivos en un directorio:</p>

      <code>file *</code>

      <h2>7z, zip, unzip</h2>

      <p>Para comprimir, y descomprimir cualquier compresor de archivo:</p>

      <code>7z a comprimir.rar archivos</code>

      <code>7z x descomprimir.rar</code>

      <p>Y si solo usas <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Formato_de_compresi%C3%B3n_ZIP">Zip</a>, también se puede esto:</p>

      <code>zip comprimir.zip archivos</code>

      <code>unzip descomprimir.zip</code>

      <h2>grep</h2>

      <p>Localiza palabra dentro de un archivo. O localizar frases dentro de un archivo. También localizar palabra al interior de todos los archivos del actual directorio:</p>

      <code>grep palabra archivo</code>

      <code>grep 'frase larga' archivo</code>

      <code>grep palabra *</code>

      <p>Localiza dos o más palabras dentro de un archivo (-e). También buscar palabras incluidas con mayúsculas (-i). O mostrar las filas de texto bajo palabra, por ejemplo 5 filas (-A). O mostrar las 3 filas arriba de palabra (-B):</p>

      <code>grep -e palabra1 -e palabra2 archivo</code>

      <code>grep -i palabra archivo</code>

      <code>grep palabra -A 5 archivo</code>

      <code>grep palabra -B 3 archivo</code>

      <p>Localiza recursivamente palabra en carpeta con archivos (-r). O localiza palabra de otro comando:</p>

      <code>grep -r palabra /carpeta</code>

      <code>history | grep palabra</code>

      <h2>sed</h2>

      <p>Reemplazar palabra o carácter en un archivo de texto, y el resultado en archivo2. O reemplazar varias palabras a la vez:</p>

      <code>sed 's/vieja/nueva/g' archivo &gt; archivo2</code>

      <code>sed 's/vieja/nueva/g ; s/vieja2/nueva2/g' archivo &gt; archivo2</code>

      <p>Si el texto tuviera barras diagonales "/", se pueden usar barras verticales o diagonales invertidas "| \" como reemplazo, por ejemplo para borrar todas las cursivas "&lt;i&gt; y &lt;/i&gt;" dentro de un subtitulo. Y usando diagonales invertidas:</p>

      <code>sed 's|&lt;i&gt;||g ; s|&lt;/i&gt;||g' sub.srt &gt; sub2.srt</code>

      <code>sed 's\vieja\nueva\g' archivo &gt; archivo2</code>

      <p>Útil para eliminar lineas, por ejemplo borrar las 4 primeras lineas (1,4d). Borrar las lineas que contengan palabra (/d). O dejar las lineas que contengan palabra (/!d). Y borrar la última linea ($d):</p>

      <code>sed '1,4d' archivo &gt; archivo2</code>

      <code>sed '/palabra/d' archivo &gt; archivo2</code>

      <code>sed '/palabra/!d' archivo &gt; archivo2</code>

      <code>sed '$d' archivo &gt; archivo2</code>

      <p>O también mostrar una linea completa junto con cat, por ejemplo la 4ta linea (-n 4p). Mostrar lineas por separado, lineas 2 y 6 (2p ; 6p). Si quisiéramos cambiar palabra solo en la 3ra linea (3s). También agregar una linea en la 5ta linea y empujar las demás hacia abajo (5i). O reemplazar todo el texto de la 6ta linea (6c). Y agregar una nueva linea después la 7ma linea, creando una nueva 8va linea (7a):</p>

      <code>cat archivo | sed -n '4p'</code>

      <code>sed -n '2p ; 6p' archivo &gt; archivo 2</code>

      <code>sed '3s/vieja/nueva/g' archivo &gt; archivo2</code>

      <code>sed '5i\Linea agregada' archivo &gt; archivo2</code>

      <code>sed '6c\Linea reemplazada' archivo &gt; archivo2</code>

      <code>sed '7a\Linea agregada después' archivo &gt; archivo2</code>

      <p>Para sobreescribir el mismo archivo sin crear otro archivo usen -i. Y si quieren sumar diferentes ordenes usen -e:</p>

      <code>sed -i '1d' archivo</code>

      <code>sed -e '1c\Linea reemplazada' -e '2i\Linea agregada' archivo &gt; archivo2</code>

      <p>Pegar la 1ra linea con la 2da linea, y así consecutivamente en par, la 3ra con la 4ta, la 5ta con la 6ta, etc. Agregar palabra al inicio de cada linea (s/^). O agregar palabra al final de cada linea (s/$). Agregar una linea al final, la cola del archivo ($a). Y dar saltos de linea (creando una nueva linea) cada vez que se tope con el carácter de doble comillas " (también puede ser otro carácter):</p>

      <code>sed 'N;s/\n/ /' archivo &gt; archivo2</code>

      <code>sed 's/^/palabra/' archivo &gt; archivo2</code>

      <code>sed 's/$/palabra/' archivo &gt; archivo2</code>

      <code>sed '$a\Linea al final' archivo &gt; archivo2</code>

      <code>sed 's/"/\n/g' archivo &gt; archivo2</code>

      <h2>cut</h2>

      <p>Para seleccionar cantidad de caracteres a mostrar, por ejemplo que muestre solo desde el carácter 5 al 10 en todas las lineas del archivo (5-10). También que muestre desde el carácter 5 en adelante en cada línea (5-). Que muestre solo los primeros 3 caracteres (-3). O sumar dos sentencias, la primera hasta el carácter 5 y la segunda desde el carácter 20 (-5,20-):</p>

      <code>cut -c 5-10 archivo</code>

      <code>cut -c 5- archivo</code>

      <code>cut -c -3 archivo</code>

      <code>cut -c -5,20-</code>

      <p>Es útil usando grep si hay demasiado texto y solo queremos pocas lineas:</p>

      <code>grep palabra archivo | cut -c 5-10</code>

      <p>Se pueden usar delimitadores, por ejemplo hasta la coma ',' (también se pueden otros / | # @, etc). Mostrar solo la 4ta oración después de la coma (-f 4). O mostrar solo la 4ta y 6ta oración después de la coma (-f 4,6). O mostrar la 4ta oración e incluir todo lo que aparezca entre medio con la 6ta oración (-f 4-6):</p>

      <code>cut -d ',' -f 4 archivo</code>

      <code>cut -d ',' -f 4,6 archivo</code>

      <code>cut -d ',' -f 4-6 archivo</code>

      <h2>head, tail</h2>

      <p>Con head se pueden ver las primeras lineas de un texto, digamos las 3 primeras lineas (-n 3). Con tail se pueden ver las últimas lineas, digamos las 2 últimas lineas (-n 2). O simplemente mostrar las últimas lineas (10 por defecto) de otro comando:</p>

      <code>head -n 3 archivo</code>

      <code>tail -n 2 archivo</code>

      <code>history | tail</code>

      <h2>find, locate</h2>

      <p>Encuentra archivos y carpetas en cualquier directorio recursivamente (/ruta -name). O buscar un tipo de archivo determinado en el directorio actual recursivamente (. -name):</p>

      <code>find /ruta -name palabra</code>

      <code>find . -name *.jpg</code>

      <p>Busca archivos por el sistema mostrando todas sus rutas:</p>

      <code>locate palabra</code>

      <h2>nano, echo, cat, alias</h2>

      <p>El editor de texto fácil y entendible, solo para crear un archivo y ponerse a escribir (Guardar: Ctrl + O. Salir: Ctrl + X). O lee y edita el código <abbr title="HyperText Markup Language">HTML</abbr> de un sitio:</p>

      <code>nano archivo</code>

      <code>nano *.html `wget www.web.com`</code>

      <p>Para crear y agregar más texto a una nota/archivo (para reemplazar todo lo escrito solo usa una flecha: &gt;). Y cat para mostrar texto de archivos directo en la terminal. O también enumerar las lineas de un texto (-n):</p>

      <code>echo "Texto" &gt;&gt; notas</code>

      <code>cat archivo</code>

      <code>cat -n archivo</code>

      <p>Útil para dar un nombre corto a comandos muy largos, y ser usado después (pueden guardar manualmente sus alias creando el archivo ~/.bash_aliases</p>

      <code>alias comando="comandos con ordenes muy largas"</code>

      <h2>iconv</h2>

      <p>Permite cambiar la <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Codificaci%C3%B3n_de_caracteres">codificación de caracteres</a> de un archivo de texto, por ejemplo cambiar un subtitulo <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/UTF-8">UTF-8</a> a un <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/ISO_8859-15">ISO-8859-15</a> para compatibilidad occidental de caracteres en español:</p>

      <code>iconv -f UTF-8 -t ISO-8859-15 sub1.srt &gt; sub2.srt</code>

      <h2>rm, trash-cli</h2>

      <p>Para eliminar definitivamente varios archivos que terminen o empiecen con la misma palabra. O borrar todos los archivos en el directorio actual (sin tocar las carpetas). O solo con extensiones especificas:</p>

      <code>rm *rchivo archiv*</code>

      <code>rm *</code>

      <code>rm *.jpg</code>

      <p>Para eliminar una carpeta se debe hacer recursivamente (-r). También eliminar todas las carpetas y archivos sueltos sin indicar nombres en el directorio actual (-r *):</p>

      <code>rm -r carpeta</code>

      <code>rm -r *</code>

      <p>Mandar archivos a la papelera (trash). Ver lo que hay en la papelera (trash-list). Y eliminar definitivamente lo que hay en la papelera (trash-empty):</p>

      <code>trash archivo</code>

      <code>trash-list</code>

      <code>trash-empty</code>

      <h2>cp, gcp</h2>

      <p>Copia archivos rápidamente dentro del sistema o otros dispositivos (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/respaldando-rsync-cp-pv.html">cp es más rápido que rsync</a>, pero sin información de transferencias y copia archivos aunque existan en destino). También copia recursivamente carpetas (-r). Y copiar todo el contenido del actual directorio:</p>

      <code>cp archivo /destino</code>

      <code>cp -r carpeta /destino</code>

      <code>cp -r * /destino</code>

      <p>Acá tenemos a gcp que se comporta igual que cp, pero con información de transferencias. Y copia recursivamente:</p>

      <code>gcp archivo /destino</code>

      <code>gcp -r carpeta /destino</code>

      <h2>pv, bar</h2>

      <p>Con pv y bar se puede ver información de transferencia (aunque no están hechos para copiar, se usa casi igual), pero hay que poner el nombre del destinatario, no solo la ruta:</p>

      <code>pv archivo &gt; /destino/archivo</code>

      <code>bar archivo &gt; /destino/archivo</code>

      <h2>mv, mmv</h2>

      <p>Para renombrar un archivo. O mover archivos de lugar:</p>

      <code>mv viejo nuevo</code>

      <code>mv origen /destino</code>

      <p>Renombrar archivos masivamente (conservando extensión). Renombrar extensión masivamente (de .jpg a .png). Poner extensión a archivos sin extensión (a .txt):</p>

      <code>mmv "viejos*" "nuevos#1"</code>

      <code>mmv "*.jpg" "#1.png"</code>

      <code>mmv "archivos*" "archivos#1.txt"</code>

      <h2>pycp, pymv</h2>

      <p>Lo mismo que cp (aunque <a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/respaldando-rsync-cp-pv.html">es más lento que cp</a>) y mv, pero con una barra de progreso e información de transferencia (instala python-pip, y luego: sudo pip install pycp):</p>

      <code>pycp archivo /destino</code>

      <code>pymv archivo /destino</code>

      <p>Si están transfiriendo una carpeta con muchos archivos usen -g para que aparezca una sola barra y no múltiples (no necesita opción de recursiva):</p>

      <code>pycp -g carpeta /destino</code>

      <h2>cd</h2>

      <p>Con cd se pueden escalar directorios. También ir a uno nuevo, como raíz (/). O ir al home (~), también se vuelve al home simplemente escribiendo solo cd. Y retroceder un nivel:</p>

      <code>cd directorio</code>

      <code>cd /</code>

      <code>cd ~</code>

      <code>cd ..</code>

      <h2>ls, wc</h2>

      <p>Para ver el tamaño de los archivos (-sh). Ver los permisos/dueños (-l). Y ver todos los archivos ocultos (-a) (se pueden combinar):</p>

      <code>ls -sh</code>

      <code>ls -l</code>

      <code>ls -a</code>

      <p>Localizar archivo que comience con una palabra. O mostrar solo con extensión .jpg. También que muestre solo con algunas extensiones (*.{jpg,gif,png}).</p>

      <code>ls archiv*</code>

      <code>ls *.jpg</code>

      <code>ls *.{jpg,gif,png}</code>

      <p>Combinando ls + wc se puede contar la cantidad de archivos y carpetas de un directorio. Y que también sume los archivos ocultos (-A) recursivamente en las demás carpetas (-R):</p>

      <code>ls | wc -l</code>

      <code>ls -AR | wc -l</code>

      <p>Listar y usar grep para mostrar solo los archivos que usen esa palabra. Y recursivamente (-R):</p>

      <code>ls | grep palabra</code>

      <code>ls -R | grep *.jpg</code>

      <h2>du</h2>

      <p>Con du se puede ver el peso de todos los directorios de una carpeta (-sh *). O el peso total del directorio actual (-sh):</p>

      <code>du -sh *</code>

      <code>du -sh</code>

      <p>Con sort se puede listar el peso de menor a mayor (al revés: -hr). O ver el peso que ocupa de cada app en el disco en macOS:</p>

      <code>du -sh * | sort -h</code>

      <code>du -sh /Applications/*</code>

      <h2>ncdu</h2>

      <p>Muy parecido a du pero navegable a través de los directorios:</p>

      <code>ncdu</code>

      <h2>tree</h2>

      <p>Permite ver el árbol de los directorios que se encuentran dentro. Y mostrar un tipo de archivo predeterminado (-P):</p>

      <code>tree -d directorio</code>

      <code>tree -P *.jpg directorio</code>

      <h2>chmod, chown</h2>

      <p>Modificar permisos de un archivo (u: usuario, g: grupo, o: otros, a: todos, r: leer, w: escribir, x: ejecutar), con signo "+" sumas permisos, con signo "-" quitas permisos (<a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2009/permisos-de-usuario-en-linux.html">guía extensa</a>). Y cambiar al dueño de un archivo (chown):</p>

      <code>chmod ugoa+rwx archivo</code>

      <code>chown usuario:usuario archivo</code>

      <h2>apt</h2>

      <p>El poderoso <abbr title="Advanced Packaging Tool">APT</abbr> que desde la <a href="https://web.archive.org/web/20200901184022/https://mvogt.wordpress.com/2014/04/04/apt-1-0/">versión 1.0</a> puede usar también 'apt orden'. Para sistemas basados en Debian, como <a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2013/el-futuro-unificado-de-ubuntu.html">Ubuntu</a> 14.04 LTS y <a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2014/probando-elementary-os-freya-beta.html">elementary OS Freya</a>. Para actualizar la lista de software (update). Y actualizar sistema (upgrade):</p>

      <code>sudo apt update</code>

      <code>sudo apt upgrade</code>

      <p>Instalar software (install). Y remover software (remove):</p>

      <code>sudo apt install nombre</code>

      <code>sudo apt remove nombre</code>

      <p>Buscar software (search). Y ver información de un paquete/app (show):</p>

      <code>apt search nombre</code>

      <code>apt show nombre</code>

      <h2>brew</h2>

      <p><a href="https://web.archive.org/web/20200901184022/https://cont3mpo.github.io/post/2015/os-x-y-homebrew.html">Homebrew es usado solo en macOS</a>. Puedes instalar, remover y mantener actualizadas tus apps CLI, y apps de interfaz que encuentres en sus repositorios</p>

      <code>brew install nombre</code>

      <code>brew-cask install nombre (apps gráficas)</code>

      <p>Y mantener actualizado:</p>

      <code>brew update</code>

      <code>brew upgrade</code>

      <h2>open</h2>

      <p>En macOS puedes abrir un archivo con open y lo abrirá con su app predeterminada:</p>

      <code>open archivo</code>

      <h2>nmap, arp-scan</h2>

      <p>Para ver a todos los que están conectados a tu Red de Área Local (<abbr title="Local Area Network">LAN</abbr>), incluidos los con Wi-Fi (aparece la <abbr title="Internet Protocol">IP</abbr>, <abbr title="Media Access Control Address">MAC</abbr> y el fabricante):</p>

      <code>sudo nmap -sP 192.168.1.0/24</code>

      <p>Con arp-scan se puede automatizar el proceso, mostrará las IPs y dirección de hardware de todos los demás conectados a la Red de Área Local. Y si estás en un notebook usa el Wi-Fi (wlan0):</p>

      <code>sudo arp-scan -l</code>

      <code>sudo arp-scan -l -I wlan0</code>

      <h2>nmcli, iwlist</h2>

      <p>Ver la lista de señales Wi-Fi cercanas:</p>

      <code>nmcli -p dev wifi list</code>

      <p>Para ver las señales Wi-Fi cercanas con información detallada:</p>

      <code>sudo iwlist wlan0 scan</code>

      <h2>ifconfig, iwconfig, wavemon</h2>

      <p>Para ver cuantos datos has descargado (RX) y subido (TX) a Internet desde que iniciaste la sesión actual. Por Ethernet (eth0) y Wi-Fi (wlan0):</p>

      <code>ifconfig eth0 | grep Bytes</code>

      <code>ifconfig wlan0 | grep Bytes</code>

      <p>Para ver la calidad de señal Wi-Fi actual (70 máx), y el nivel de señal <a href="https://web.archive.org/web/20200901184022/http://es.wikipedia.org/wiki/DBm">dBm</a> (prueben acercándose y alejándose para ver como afecta):</p>

      <code>iwconfig wlan0 | grep Quality</code>

      <p>Con wavemon se puede monitorear la intensidad de la señal Wi-Fi y otros datos en pantalla completa:</p>

      <code>wavemon</code>

      <h2>htop, iotop, pydf</h2>

      <p>Con htop se puede monitorear el uso de procesos que están corriendo, también uso de <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento"><abbr title="Central Processing Unit">CPU</abbr></a>, <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio"><abbr title="Random-Access Memory">RAM</abbr></a> y <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Espacio_de_intercambio">Swap</a> (los que utilizan más procesamiento aparecen en la cabecera). Y con iotop puedes ver que procesos están escribiendo y leyendo en tu disco:</p>

      <code>htop</code>

      <code>sudo iotop</code>

      <p>Muy practico para estar al tanto de cuanto espacio estás ocupando o te queda en tus discos duros, particiones, pendrives o discos duros móviles:</p>

      <code>pydf</code>

      <h2>lm-sensors, hddtemp, acpi</h2>

      <p>Para ver la temperatura del procesador (Core son las CPU) (luego de instalar: sudo sensors-detect ; sudo service kmod start). Con hddtemp se monitorea la temperatura del disco duro:</p>

      <code>sensors</code>

      <code>sudo hddtemp /dev/sda</code>

      <p>Y para monitorear cuanta batería queda o se está cargando en el notebook:</p>

      <code>acpi -i</code>

      <h2>netstat, free, ps</h2>

      <p>Ver los puertos abiertos (escuchando) que está ocupando cada app:</p>

      <code>sudo netstat -plunt</code>

      <p>Ver la RAM real en uso y que está libre:</p>

      <code>free -h | grep -e usado -e cache</code>

      <p>Con ps se puede ver la lista de todos los procesos que están corriendo y el usuario que los usa. O buscar el nombre de un proceso corriendo:</p>

      <code>ps aux</code>

      <code>ps x | grep -i nombreapp</code>

      <p>Para información en un-solo-lugar de uso de cpu, ram, swap, red, procesos, instala <a href="https://web.archive.org/web/20200901184022/http://askubuntu.com/a/293447">Glances</a>.</p>

      <h2>lsblk, mount, umount</h2>

      <p>Parecido a pydf, pero muestra la jerarquía de las particiones, y puede ver los dispositivos conectados aunque no estén montados:</p>

      <code>lsblk</code>

      <p>Con mount se puede montar el dispositivo (pendrive, disco duro portátil) al ver donde está con lsblk, y con umount se puede desmontar para desconectar:</p>

      <code>sudo mount /dev/sdb1 /media/usuario/</code>

      <code>sudo umount /media/usuario/</code>

      <h2>lspci, lshw</h2>

      <p>Para ver el tipo de <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Unidad_de_procesamiento_gr%C3%A1fico"><abbr title="Graphics Processing Unit">GPU</abbr></a> (gráficos) que usa el equipo, y fabricante del modelo Wi-Fi:</p>

      <code>lspci | grep -e VGA -e Wireless</code>

      <p>Ver cada parte de todo el hardware, su fabricante y modelos en detalle. También ver solo información del procesador:</p>

      <code>sudo lshw</code>

      <code>sudo lshw | grep CPU -A 12</code>

      <h2>speedometer, speedtest-cli</h2>

      <p>Para monitorear la velocidad en la conexión, en descarga (-r) y subida (-t), en un gráfico (Wi-Fi: wlan0):</p>

      <code>speedometer -r eth0</code>

      <code>speedometer -t eth0</code>

      <p>Con <a href="https://web.archive.org/web/20200901184022/https://github.com/sivel/speedtest-cli">speedtest-cli</a> se realizan test de velocidad de descarga y subida (instala python-pip, y luego: sudo pip install speedtest-cli):</p>

      <code>speedtest-cli</code>

      <h2>ping</h2>

      <p>Ver si hay perdida de paquetes en una conexión inestable, y cuanto se demoran los paquetes en milisegundos para ir y volver (salir: Ctrl + C). O transmitir una cantidad de paquetes predeterminada (-c):</p>

      <code>ping www.google.com</code>

      <code>ping -c 5 www.google.com</code>

      <h2>whoami, who, pwd</h2>

      <p>Con whoami se puede ver el nombre del usuario actual. Con who se ven los todos los usuarios conectados. Y pwd muestra la ruta completa del directorio actual:</p>

      <code>whoami</code>

      <code>who</code>

      <code>pwd</code>

      <h2>tcpdump, whois, host</h2>

      <p>Para monitorear todo lo que pasa por el puerto 80 <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Transmission_Control_Protocol"><abbr title="Transmission Control Protocol">TCP</abbr></a> (usado en <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Hypertext_Transfer_Protocol"><abbr title="Hypertext Transfer Protocol">HTTP</abbr></a>) (Salir: Ctrl + C):</p>

      <code>sudo tcpdump tcp port 80</code>

      <p>Para ver información de dueño del dominio, servidores, y creación del dominio. Y host puede ver la <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Direcci%C3%B3n_IP"><abbr title="Internet Protocol">IP</abbr></a> del dominio:</p>

      <code>whois web.com</code>

      <code>host web.com</code>

      <h2>traceroute, dig</h2>

      <p>Muestra la ruta de viaje de un dominio a través de servidores:</p>

      <code>traceroute google.cl</code>

      Ve información de un domino DNS:

      <code>dig google.cl</code>

      <h2>tshark</h2>

      <p>O mejor conocido como <a href="https://web.archive.org/web/20200901184022/https://es.wikipedia.org/wiki/Wireshark">Wireshark</a>. Sirve para monitorear el tráfico de conexiones. Primero hay que ver el nombre de las interfaces disponibles (-D), y luego monitorear esa conexión con su nombre (-i):</p>

      <code>sudo tshark -D</code>

      <code>sudo tshark -i en0</code>

      <h2>sleep, notify-send, date</h2>

      <p>Ejecutar una orden en el tiempo dado (sleep), además con notificación (notify-send), hora (date), y música de fondo (mpv). Como un despertador:</p>

      <code>sleep 1h 30m 10s ; notify-send -u critical ¡Despierta! "$(date)" ; mpv audio.mp3</code>

      <h2>watch, alsamixer</h2>

      <p>Refresca un comando cada 2 segundos para observar cambios (1 segundo: -n 1). Por ejemplo si estuviéramos monitoreando el peso de los archivos que se están transfiriendo o bajando:</p>

      <code>watch ls -sh</code>

      <p>Con alsamixer se pueden controlar los niveles de audio de los altavoces, micrófono en captura (para cambiar a captura: TAB), y las entradas de audio en linea:</p>

      <code>alsamixer</code>

      <h2>xkill, killall, kill</h2>

      <p>Las tres formas de matar o cerrar a la fuerza apps/procesos. Con xkill se apunta con el cursor a la ventana y la mata. Con killall hay que escribir el nombre de la app. Con kill se escribe el PID de la app, que se obtiene con "ps x | grep -i nombreapp":</p>

      <code>xkill</code>

      <code>killall nombre</code>

      <code>kill pidapp</code>

      <p>Pueden seguir viendo <a href="https://web.archive.org/web/20200901184022/http://www.reddit.com/r/linux/comments/eizx9/top_linux_commands_every_linux_user_should_know/">algunas recomendaciones en Reddit</a> y visitar <a href="https://web.archive.org/web/20200901184022/http://www.reddit.com/r/commandline">/r/commandline</a>, ver un <a href="https://web.archive.org/web/20200901184022/http://ss64.com/bash/">indice de comandos</a> útiles, leer <a href="https://web.archive.org/web/20200901184022/http://www.die.net/">sus manuales</a> o de <a href="https://web.archive.org/web/20200901184022/http://manpages.ubuntu.com/">otros manuales de Ubuntu</a>, o ir <a href="https://web.archive.org/web/20200901184022/http://linuxcommand.org/lc3_learning_the_shell.php">aprendiendo más detalladamente</a>. También pueden empezar creando <a href="https://web.archive.org/web/20200901184022/http://cont3mpo.blogspot.com/2009/09/interpretar-ordenes-shell-script.html">shell scripts básicos</a> y ver comandos más complejos en <a href="https://web.archive.org/web/20200901184022/http://www.commandlinefu.com/">Commandlinefu</a>. O leer en linea el libro <a href="https://web.archive.org/web/20200901184022/http://conqueringthecommandline.com/book">Conquering the Command Line</a>. También una <a href="https://web.archive.org/web/20200901184022/http://www.oliverelliott.org/article/computing/tut_unix/">Introducción a Unix</a>, y <a href="https://web.archive.org/web/20200901184022/http://www.oliverelliott.org/article/computing/ref_unix/">100 comandos útiles</a>.</p>

      <time datetime="2014-10-25">25 de octubre, 2014</time>
    </article>
