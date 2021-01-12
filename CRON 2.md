## script1
primero se crea script1.sh con el siguiente contenido
```
#! /bin/bash
echo `date "+Hello $USER, today is %A, %B %dth, %Y and it's %H:%M:%S. I'm Sergio."` >> date.txt
```

luego se le dan los permisos pertinentes
```
chmod 777 script1.sh
```

por último hay que introducir el comando `crontab -e` para abrir la configuracion de crontab y añadir:
```
*/5 * * * 1-5 /home/ubuntu/script1.sh
```
comprobación
![comprobacion script1](img/comprobacion_crontab1.png)

---
## script2
primero se crea la carpeta en la que se meterán los backups
```
sudo mkdir /copias
```

luego se crea el script
```
#! /bin/bash
tar -cf /copias/copia.tar.gz /home/ubuntu
```
> esto creará una copia de seguridad de /home/ubuntu en /copias y la soobreescribirá en caso de que ya haya una.

luego se le dan los permisos pertinentes
```
chmod 777 script1.sh
chmod 777 /copias
```

y por último hay que introducir el comando `crontab -e` para abrir la configuracion de crontab y añadir:
```
*/15 * * * 2 /home/ubuntu/script2.sh
```
comprobación
![comprobacion script2](img/comprobacion_crontab2.png)