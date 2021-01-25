# configuración de www.apuntes.daw.net:80

> Configuración mediante fichero .htaccess.
> + Alojado en: /var/www/apuntes/.
> + Sin Fichero index.
> + Permitir mostrar índice de ficheros.
> + Pagina de error 404: /var/www/404.html.
> + Redirigir www.apuntes.daw.net/buscador/ a www.google.es.
> + Ficheros log: apuntes.error.log y apuntes.access.log

```
<VirtualHost *:80>

    ServerName www.apuntes.daw.net
    DocumentRoot /var/www/apuntes/

    Alias /apuntes /var/www/apuntes/
    <Directory /var/www/apuntes/>
        Options Indexes
        Order Allow,Deny
        Allow from all
        AllowOverride All
    <Directory/>

    Alias /error /var/www/
    ErrorDocument 404 /var/www/404.html
    ErrorLog ${APACHE_LOG_DIR}/apuntes.error.log
    CustomLog ${APACHE_LOG_DIR}/apuntes.access.log combined

<VirtualHost/>
```

dentro del fichero .htaccess:
```
Redirect "/buscador" "www.google.es"
```
<br>

# configuración de www.daw.net:443

> Alojado en: /var/www/daw/seguro/
> + Crear y utilizar el certificado daw.crt y la firma daw.key
> + Fichero index: inicio.html.
> + No permitir mostrar índice de ficheros.
> + Pagina de error 404: /var/www/404.html
> + Ficheros log: daw.ssl.error.log y daw.ssl.access.log
> + Autenticación de usuarios "Basic” con fichero de usuarios permitidos en /var/www/acceso.basic.daw

```
<VirtualHost *:80>

    ServerName www.apuntes.daw.net
    DocumentRoot /var/www/daw/seguro/

    Alias /seguro /var/www/daw/seguro/
    <Directory /var/www/daw/seguro/>
        DirectoryIndex inicio.html
        Options -Indexes
        Order allow,deny
        allow from all
        AllowOverride All
        AuthType Basic
        AuthName "Se necesita contraseña"
        AuthUserFile "/var/www/acceso.basic.daw"
        Require valid-user
    <Directory/>

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/daw.crt
    SSLCertificateKeyFile /etc/ssl/private/daw.key

    Alias /error /var/www/
    ErrorDocument 404 /var/www/404.html
    ErrorLog ${APACHE_LOG_DIR}/daw.ssl.error.log
    CustomLog ${APACHE_LOG_DIR}/daw.ssl.access.log combined

<VirtualHost/>
```