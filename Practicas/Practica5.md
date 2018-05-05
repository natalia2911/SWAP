## Practica 5
### **Replicación de bases de datos MySQL**
Hay que llevar a cabo las siguientes tareas:
### **1. Crear una BD con al menos una tabla y algunos datos. **
Empezamos creando una base de datos en mi maquina server_1 (ip:192.168.56.10):

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_00.PNG)

Creamos la base de datos llamada “contactos” (créate database contactos;), seleccionamos la base de datos creada (use contactos), y creamos la tabla datos que tendrá un nombre y un teléfono (créate table datos), insertamos un nombre y un numero que mostramos a continuación.

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_01.PNG)

Con “describe datos” mostramos la información de la tabla por columnas y terminamos saliendo de la base de datos

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_02.PNG)

### **2. Realizar la copia de seguridad de la BD completa usando mysqldump en la máquina principal y copiar el archivo de copia de seguridad a la máquina secundaria**
Creamos una copia de seguridad en un archivo .sql, para ello antes bloqueamos dicha base de datos para que nadie pueda actualizarla ni cambiar nada, hacemos la copia de seguridad y desbloqueamos la base de datos como se ve a continuación: 

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_03.PNG)

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_04.PNG)

Ahora vamos a hacer la copia de seguridad del archivo “contactosbd.sql” a la maquina secundaria, usamos como maquina secundaria nuestro server_2, es muy sencillo, desde la maquina server_2 con la orden “scp 192.168.56.10:/tmp/contactosbd.sql /tmp/” nos traemos el archivo, posteriormente comprobamos que está:

![mysql](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_05.PNG)

### **3. Restaurar dicha copia de seguridad en la segunda máquina (clonado manual de la BD), de forma que en ambas máquinas esté esa BD de forma idéntica. **
Para restaurar en la maquina server_2 la base de datos que hemos exportado, tenemos que crearla a mano, ya que el archivo contiene las sentencias que incluyen los datos, pero no ese paso.
Después de crear la base de datos, con “mysql -u root -p contactos < /tmp/contactosbd.sql” se crean las tablas de la misma como podemos ver en la imagen:

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_06.PNG)

### **4. Realizar la configuración maestro-esclavo de los servidores MySQL para la replicación de datos se realice automáticamente. **
Configuramos mysql del maestro (server_1), editamos el fichero “/etc/mysql/mysql.conf.d/mysqld.cnf” con las modificaciones que se ven a continuación:
Comentamos:  #bind-address 127.0.0.1

Des comentamos:

log_error = /var/log/mysql/error.log

server-id = 1

log_bin = /var/log/mysql/ mysql -bin.log

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_07.PNG)

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_08.PNG)

Guardamos la configuración y reiniciamos el servicio.

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_09.PNG)

Ahora nos vamos al esclavo (server_2). 

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_10.PNG)

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_11.PNG)

Guardamos la configuración y reiniciamos el servicio.

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_12.PNG)

No nos ha dado ningún error. Nos volvemos a la maquina maestro para crear un usuario y darle permisos de acceso para la replicación.

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_14.PNG)

Volvemos a la máquina esclava, entramos en mysql y le damos los datos del maestro con:

mysql> CHANGE MASTER TO MASTER_HOST='192.168.56.10',
MASTER_USER='esclavo', MASTER_PASSWORD='esclavo',
MASTER_LOG_FILE='mysql-bin.000002', MASTER_LOG_POS=980,
MASTER_PORT=3306;

Otra vez nos vamos al maestro para activar las tablas y que podamos meter nuevos datos desde el mismo:

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_16.PNG)

Para asegurarnos que todo funciona nos vamos al esclavo con la siguiente orden “start slave”, y para comprobar errores ejecutamos “show slave status\G” que nos da la siguiente salida:

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_17.PNG)

Comprobamos que todo funciona como debe y que la variable “seconds_Behind_Master” es 0, por lo que no hay ningún error.

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P5_18.PNG)


Practica realizada por Matilde Cabrera González y José María Aguilera Barea.
