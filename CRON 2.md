## script1
primero se crea script1.sh con el siguiente contenido
```
#! /bin/bash
echo `date "+Hello $USER, today is %A, %B %dth, %Y and it's %H:%M:%S. I'm Sergio."` >> date.txt
```
> esto añadirá una linea al archivo date.txt en el que aparecerá el contenido  entrecomillado( \`...\` ) del echo 

luego se le dan los permisos pertinentes
```
chmod 777 script1.sh
```

por último hay que introducir el comando `crontab -e` para abrir la configuración de crontab y añadir:
```
*/5 * * * 1-5 /home/ubuntu/script1.sh
```
comprobación
![comprobacion script1](https://raw.githubusercontent.com/sergio9929/ejercicios-dweb/main/img/comprobacion_crontab1.png?token=AHC74HKTFAWCNR4N5K4UNMK77WXUQ)

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
chmod 777 script2.sh
chmod 777 /copias
```

y por último hay que introducir el comando `crontab -e` para abrir la configuración de crontab y añadir:
```
*/15 * * * 2 /home/ubuntu/script2.sh
```
comprobación
![comprobacion script2](https://raw.githubusercontent.com/sergio9929/ejercicios-dweb/main/img/comprobacion_crontab2.png?token=AHC74HL63CFJRG4VLD56ROC77WXUU)