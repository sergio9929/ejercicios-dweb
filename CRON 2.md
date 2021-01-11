hay que dar permisos de ejecucion al archivo
```
chmod 777 script1.sh
```

hay que poner a root como propietario
```
chown root script1.sh
```

hay que escribir `crontab -e` para abrir la configuracion de crontab y escribir:
```
*/5 * * * 1-5 /home/ubuntu/script1.sh
*/15 * * * 2 /home/ubuntu/script2.sh
```