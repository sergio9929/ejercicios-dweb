# Apache2

## Ficheros de configuración y directivas en Linux
1. **¿Cuál es la ruta a los ficheros de configuración de apache?** /etc/apache2
1. **¿Cuál es el fichero de configuración principal?** apache2.conf
1. **¿Que son las directivas "include" que aparecen en el fichero de configuración principal?** Permite incluir otros archivos de configuración
1. **¿Que contiene el fichero ports.conf?** Los puertos a los que Apache escuchará y en que casos.
1. **¿Que contiene el fichero envvars?** Las variables de entorno de Apache
1. **¿Cuál es el uso de las carpetas "sites-avaliable" y "sites-enabled"'?** Es donde se guardan los virtual hosts disponibles y los que están habilitados.

## Define para que se utilizan las siguientes
- **ServerRoot:** define la ruta del directorio en el que se aloja el servidor Apache. `ServerRoot /etc/apache2`
- **ServerAdmin:** define la dirección de correo electrónico del administrador del servidor. `ServerAdmin admin@ejemplo.com`
- **ServerName:** define el nombre del host. `ServerName www.ejemplo.com`
- **ServerAlias:** sirve para dar nombres alternativos a hosts. `ServerAlias *.ejemplo.com`
- **User:** define el usuario al cual pertenece el proceso de Apache.
- **Include:** permite incluir otros archivos de configuración. `Include /etc/apache2/ports.conf`
- **Group:** define el grupo al cual pertenece el proceso de Apache.
- **KeepAlive:** permite habilitar KeepAlive para que la conexión con el cliente quede activa por un periodo y no cree una nueva conexión continuamente, esto mejora las latencias y carga de imagenes. `KeepAlive On`
- **Files:** Las directivas que se incluyan dentro de Files sólo se aplican a ese archivo. `<Files "ejemplo.html"> aquí van las directivas </Files>`
- **Location:** las directivas del bloque Location se aplícan únicamente en el ámbito de la URL indicada en la etiqueta. `<Location /imagen> aquí van las directivas </Location>`
- **ErrorLog:** indica qué fichero tiene el registro de errores. `ErrorLog /var/log/httpd/error_log`
- **Listen:** define los puertos o IPs desde los que se escucharán peticiones. `Listen 192.168.1.10:8080`
- **Alias:** sirve para dar nombres alternativos a rutas. `Alias "/imagen" "/ruta/larga/inicial/imagen"`
- **Redirect:** sirve para redireccionar en caso de que la web se haya movido. `Redirect /imagen http://otrodirectorio.ejemplo.com/imagen`
- **ErrorDocumet 404:** cuando de el error 404 permite hacer una de estas 4 cosas
    1. mostrar el mensaje de error. `ErrorDocument 500 http://foo.example.com/cgi-bin/tester`
    1. mostrar un mensaje de error personalizado. `ErrorDocument 404 /cgi-bin/bad_urls.pl`
    1. redireccionar a una URL local. `ErrorDocument 401 /error.html`
    1. redireccionar a una URL externa. `ErrorDocument 403 "No tienes acceso en este momento"`
- **Options:** la directiva Options contiene la lista de características que están disponibles para un determinado directorio. Las que no están disponibles van precedidas de un signo -. `Options Indexes -FollowSymLinks`
- **\<VirtualHost>…\</VirtualHost>:** las directivas que se incluyan dentro de VirtualHost sólo se aplican a ese host virtual. `<VirtualHost 192.168.1.10> aquí van las directivas </VirtualHost>`
- **\<Directory>…\</Directory>:** las directivas que se incluyan dentro de Directory sólo se aplican a ese directorio, los subdirectorios y los contenidos. `<Directory /var/www/html/imagen> aquí van las directivas </Directory>`
- **DocumentRoot:** define la ruta de el directorio local donde reside la información del sitio web. `DocumentRoot /var/www/html`
- **DirectoryIndex:** Especifica el fichero por defecto que se servirá para cada directorio. Si no se especifica ninguno en la URL, por defecto será index.html. `DirectoryIndex ejemplo.html`