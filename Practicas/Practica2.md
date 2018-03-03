## Practica 2

### **Clonar la información de un sitio web**

Hay que llevar a cabo las siguientes tareas

**1. Probar el funcionamiento de la copia de archivos por ssh.**


	Para ello vamos a usar tar para crear un archivo “tar.tgz” directamente en el equipo destino. Visualizamos donde vamos a crear el archivo, no está.
![tar](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_1.PNG)

	Ejecutamos  “tar czf - home/serverdos | ssh severdos@192.168.56.20 ‘cat > ~/tar.tgz’ “ y vemos el resultado.
![tar](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_2.PNG)


**2. Clonado de una carpeta entre las dos máquinas.**

	Hemos instalado la herramienta rsync, hemos cambiado el contenido de “/var/www/” de una de las maquinas para ver el cambio cuando clonemos la carpeta.

![rsync](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_3.PNG)

	Clonamos la carpeta mencionada de “ubuntu1” a la máquina “ubuntu2”.

![rsync](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_4.PNG)


**3. Configuración de ssh para acceder sin que solicite contraseña.**

	Seguimos el guion de la práctica, “ssh-keygen -b 4096 -t rsa” genera clave (llave),  “ssh-copy-id 192.168.56.10” para acceder desde la maquina principal a la secundaria sin necesidad de que solicite contraseña.

![ssh](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_5.PNG)

	Cambiamos los nombres de las maquinas para diferenciarlas claramente cuando se conectan ”sudo hostnamectl set-hostname “nuevonombre””, y comprobamos que se conecta sin necesidad de contraseña. 

![ssh](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_6.PNG)


**4. Establecer una tarea en cron que se ejecute cada hora para mantener
actualizado el contenido del directorio /var/www entre las dos máquinas.**

	A partir de ahora la maquina “ubuntu2” hará de server principal. Accedemos a “/etc/crontab”, en crontab están las tareas que se ejecutan de forma automatizada. Añadimos desde el servidor principal (ubuntu2) un proceso “rsync -avz -e ssh 192.18.56.10:/var/www/ /var/www/”, para que cada hora copie el contenido de “/var/www” del server secundario (donde estamos trabajando), al servidor principal que es el que se muestra al público.
![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_7.PNG)

	Para probar que lo hace bien, lo ponemos momentáneamente para que se copie cada minuto, capturamos la pantalla con algún cambio en el equipo “ubuntu1”.
![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_8.PNG)

	Esperamos un minuto y refrescamos la información, los cambios se efectúan en el equipo principal (ubuntu2).
![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P2_9.PNG)

Practica realizada por Matilde Cabrera.
