# ¿Qué hace cada línea de CRON?
## 30 * * * * /home/prueba.sh
```
el script se ejecuta cada hora a y media
```

## 30 20 * * * /home/prueba.sh
```
el script se ejecuta a las 20:30 cada dia
```

## 30 20 * * 1-5 /home/prueba.sh
```
el script se ejecuta a las 20:30 de lunes a viernes
```

## 30 20 10,20 * * /home/prueba.sh
```
el script se ejecuta a las 8:30 los dias 10 y 20 de cada mes
```

## */15 * * * * /home/prueba.sh
```
el script se ejecuta cada 15 minutos
```

## @daily /home/prueba.sh
```
el script se ejecuta a diario a las 00:00
```

## @mountly /etc/backup.sh
```
el script se ejecutaria cada mes si @mountly estuviera bien escrito
```

## 30 20 * * Mon-Fri /etc/test.sh
```
el script se ejecuta a las 20:30 de lunes a viernes
```

## 1 0 1-7 * * [ "$(date '+%a')" = "Fri" ] && /etc/backup.sh
```
ejecuta /etc/backup.sh y comprueba si es viernes a las 00:01 del dia 1 al 7 de cada mes
```