## Practica 4

### **Asegurar la granja web**
Hay que llevar a cabo las siguientes tareas:
### **1. Tenemos que generar e instalar un certificado auto firmado para cada una de las máquinas y para el balanceador**
Empezamos por la maquina server 1 cuya dirección ip es 192.168.56.10. Seguimos el guion de la práctica donde se indica lo que sigue:
Orden “a2enmod ssl” para habilitar el módulo ssl.
 ![a2enmod](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_01.PNG)

Reiniciamos el servicio apache:
![apache](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_02.PNG)

Creamos el directorio ssl en la ruta “etc/apache2/ssl”, nosotros ya lo teníamos creado de antes así que nos saltamos el paso.
Configuramos el dominio para los certificados: (Nos ha pedido una serie de datos que rellenamos según el guion de prácticas).

![openssl](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_03.PNG)

Editamos el archivo de configuración del sitio default-ssl, orden “sudo nano /etc/apache2/sites-abailable/default-ssl”, y agregamos las líneas que se ven:
![ssl](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_04.PNG)

Activamos el sitio default-ssl editado en el paso anterior:
![ssl](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_05.PNG)

Reiniciamos apache “service apache2 reload” y desde el navegador comprobamos una petición:
![ssl](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_06.PNG)

Ahora lo comprobamos desde el mismo servidor:

![ssl](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_07.PNG)

Una vez conseguido su funcionamiento en la maquina 1, copiamos su certificado en la maquina 2 y en el balanceador. Para ello primero hemos tenido que cambiar el permiso del root. Ejecutamos “sudo nano /etc/ssh/sshd_config”, una vez dentro buscamos la línea “PermitRootLogin prohibit-password” y la cambiamos por “PermitRootLogin yes”, posteriormente reiniciamos el servicio sshd con “service sshd restart”. 
Vamos a la maquina dos, hay varias formas de copiar los archivos, hemos elegido la siguiente:
![ssh](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_08.PNG)

De igual forma pasamos el certificado al balanceador nginx, este no tiene creada la carpeta ssl, así que antes de nada hay que crearla y ya podremos ejecutar la orden anterior sin problema.
Hemos comprobado que podemos acceder desde el balanceador a ambas maquinas con “curl -k https://ip_de_cada_maquina”, de igual forma entre las maquinas.
Para acceder desde una tercera maquina al balanceador y que nos sirva peticiones, hemos tenido que modificar el siguiente archivo, para que acepte peticiones https:

![script](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_14.PNG)

Comprobamos que desde el navegador podemos ver tanto las peticiones http como https.

### **2. Configurar las reglas del cortafuegos con IPTABLES a la maquina final 1**
Creamos un script que se ejecute en el arranque del sistema de la maquina 1, como aconseja en el guion de la práctica. Script:
![script](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_09.PNG)

Tenemos que ejecutar el anterior script cada vez que la maquina se inicie, es decir, con el resto de los componentes del sistema. Para ello, con la orden mv, movemos el script a “init.d”, y como se ve a continuación comprobamos que está :

![init](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_10.PNG)

Añadimos a crontab que se ejecute cada vez que se inicie sesión con la orden “reboot”

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_11.PNG)

Hemos comprobado que seguimos viendo la pagina https://hola.html del servidor que hemos modificado el cortafuegos desde otra máquina diferente. Además, hemos comprobado los puertos que hay abiertos y que demonios los tienen en uso:

![crontab](https://github.com/mati3/SWAP/blob/master/Imagenes/P4_12.PNG)

Practica realizada por Matilde Cabrera González y José María Aguilera Barea.
