# Ejercicio T3.1:
### Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.

Comando Route para Windows:
El comando Route se utiliza para visualizar y modificar la tabla de rutas. Route print muestra una lista con las rutas actuales conocidas por IP para el host. Route add se utiliza para añadir rutas a la tabla,  route delete se utiliza para borrar rutas de la tabla. Nótese que las rutas añadidas a la tabla no se harán persistentes a menos que se especifique el modificador –p, por lo que solo permanecerán en dicha tabla hasta el siguiente reinicio de la máquina. Para que dos hosts intercambien datagramas IP, ambos deberán tener una ruta al otro, o utilizar un gateway por omisión que conozca una ruta. Normalmente, los routers intercambian información entre ellos utilizando un protocolo como RIP (Routing Information Protocol) u OSPF (Open Shortest Path First). Puesto que NT no ha proporcionado tradicionalmente una implementación para estos protocolos, si se deseaba utilizar un equipo como router, debía configurarse manualmente su tabla de rutas. El comando route presenta los siguientes formatos: route [-f] [-p] [comando [destino]] [MASK máscara de red] [puerta de acceso] [METRIC métrica] [IF interfaz] - -f: Borra las tablas de enrutamiento de todas las entradas de la puerta de acceso. Si se usa éste junto con uno de los comandos, las tablas se borran antes de ejecutar el comando.

-p: Cuando se usa con el comando ADD, hace una ruta persistente en el inicio del sistema. De forma predeterminada, las rutas no se conservan cuando se reinicia el sistema. Cuando se usa con el comando PRINT, muestra la lista de rutas persistentes registradas. Se omite para todos los otros comandos, que siempre afectan las rutas persistentes apropiadas. Esta opción no está disponible en Windows 95. - Comando: Puede ser uno de los siguientes: PRINT: Imprime una ruta ADD Metric if : Agregar una ruta DELETE : Elimina una ruta CHANGE Metric if : Modifica una ruta existente - MASK : Especifica que el siguiente parámetro es el valor "máscara de red".
METRIC: Especifica la métrica, es decir, el costo para el destino. - if : Especifica la dirección IP de la interfaz sobre la que es accesible el destino. - máscara de red: Especifica un valor de máscara de subred para esta entrada de ruta. Si no se especifica, el valor predeterminado es 255.255.255.255. - destino: Especifica el host. - puerta de acceso: Especifica la puerta de acceso. - Interfaz: El número de interfaz para la ruta especificada. Todos los nombres simbólicos usados para el destino se buscan en el archivo de la base de datos de la red NETWORKS. Los nombres simbólicos para la puerta de acceso se buscan en el archivo de la base de datos de nombres de hosts HOSTS. Si el comando es PRINT o DELETE. El destino o la puerta de acceso pueden ser un comodín (el comodín se especifica como una estrella "*") o bien se puede omitir el argumento de la puerta de acceso. Si Dest contiene un carácter * o ?, se le considera como un modelo de núcleo y sólo se imprimen las rutas de destino coincidentes. El carácter "*" coincide con cualquier cadena y "?" coincide con cualquier carácter. Ejemplos: 157.*.1, 157.*, 127.*, *224*. Si no se da IF, intenta buscar la mejor interfaz para una puerta de acceso determinada.

Herramienta grafica de Servicio Enrutamiento y acceso remoto (RemoteAccess) para Windows 10, Windows 8, Windows 7, Windows Vista

Descripción

Ofrece servicios de enrutamiento a empresas en entornos de red de área local y extensa.

Propiedades para Windows 10

Nombre inicio servicio	localSystem

Archivo	%WinDir%\System32\mprdim.dll

Error	normal

Tipo	share

Nombre ruta binario	%WinDir%\System32\svchost.exe -k netsvcs

Nombre para mostrar	Enrutamiento y acceso remoto

Nombre	RemoteAccess

Dependencias

Enrutamiento y acceso remoto depende de los siguientes componentes del sistema:

Administrador de conexiones de acceso remoto.
Llamada a procedimiento remoto (RPC).
Motor de filtrado de base-
Servicio HTTP. 
Creación del script para activar enrutamiento
Para activar el enrutamiento en un sistema Linux, tan solo basta con poner a '1' la variable ip_forward del sistema, es decir, basta con ejecutar desde una consola de root:

### linux
Activar el enrutamiento en un sistema Linux sudo echo "1" > /proc/sys/net/ipv4/ip_forward
Posteriormente tendríamos que configurar el filtrado para que acepte el redireccionamiento de paquetes desde dentro hacia fuera de nuestra red y mediante NAT permita que los PCs de la red interna naveguen con la dirección IP 'publica' del servidor. Supongamos que el router Linux tiene una tarjeta (eth0) configurada con la IP 192.168.1.2/24 y conectada al router, cuya IP es 192.168.1.1/24, y por otro lado, tenemos otra tarjeta (eth1) configurada con la ip 10.0.0.1/8 y conectada al switch para dar servicio a nuestra red interna que utiliza el rango 10.0.0.0/8. Nuestro esquema sería como el que vemos en la siguiente figura:

 

#### Router Linux

Tendríamos que indicar que se acepten todos los paquetes que son para reenviar, es decir, aquellos que llegan a nuestra máquina pero que no es ella la destinataria. Para ello, tendríamos que aceptar los paquetes de tipo FORWARD, como veremos en la siguiente sección. Por otro lado, tendríamos que indicar que los paquetes que llegan desde nuestra red interna (-s 10.0.0.0/8) y que salgan por la interfaz eth0 hacia el router (-o eth0), después de enrutarlos en nuestra máquina (POSTROUTING), debemos enmascararlos (MASQUERADE), es decir, hacer NAT. Los comandos a ejecutar serían:

Haciendo NAT en el servidor
sudo iptables -A FORWARD -j ACCEPT
sudo iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -o eth0 -j MASQUERADE
Podríamos realizar un script que activara el enrutamiento y el NAT y otro para desactivarlo:

activar-enrutamiento.sh
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -A FORWARD -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -o eth0 -j MASQUERADE 

desactivar-enrutamiento.sh
echo "0" > /proc/sys/net/ipv4/ip_forward
Así, nuestro servidor se convertiría en un router. Si todas las comunicaciones de la red pasan por nuestro servidor, podremos tenerlas controladas, como veremos en las siguientes secciones.
Crear y eliminar rutas fijas
Cuando activamos el enrutamiento en Linux, nuestra máquina se convierte en un router automático, de forma que todo lo que entre por la interfaz eth0 con destino a una red diferente de la definida en eth0, lo reenviará por la interfaz eth1 y de igual forma, todo lo que entre por la interfaz eth1 con destino a una red diferente de la definida en eth1, lo reenviará por la interfaz eth0. Es el funcionamiento normal de un router, enrutar todo.

En algunos casos, puede que nos interese que ciertos paquetes salgan por una interfaz concreta. Por ejemplo, supongamos que en nuestra red disponemos de dos conexiones ADSL independientes, una para dar servicio de conexión a Internet al servidor (interfaz de producción) y otra, para conectarnos desde nuestra casa al servidor, para realizar tareas de administración (interfaz de administración).Supongamos que la interfaz eth0 está conectada al router ADSL de producción y la interfaz eth1 está conectada al router ADSL para realizar tareas de administración.

 

##### Rutas fijas
Lo normal es que la interfaz eth0 tenga configurada como puerta de enlace la IP del router de conexión a Internet, pero la interfaz eth1 no debería tener configurada la puerta de enlace, para que no exista tráfico hacia Internet por dicha interfaz. Si en el ADSL de nuestra casa tenemos IP fija, podemos crear una ruta para que cuando la IP destino sea la IP fija de nuestra casa, los paquetes se enruten por eth1 en lugar de hacerlo por eth0. Ejemplo, si nuestra IP de casa es 80.58.12.27, el comando a ejecutar será:

Crear una ruta para una IP concreta
sudo route add 80.58.12.27 eth1
En lugar de una IP concreta, quizás nos interese crear una ruta para toda una red. Supongamos que queremos que cuando la IP destino sea una IP del CNICE, salga por la interfaz eth1. Teniendo en cuenta que el rango de IPs públicas del CNICE es 192.144.238.0/24, el comando a ejecutar sería:

Crear una ruta para una red concreta
sudo route add -net 193.144.238.0/24 eth1
Si queremos eliminar una ruta, utilizaremos el parámetro 'del' seguido de la IP o la red destinataria. Ejecutaríamos el siguiente comando:

Eliminar una ruta
sudo route del -net 193.144.238.0/24
Si queremos ver la configuración de la tabla de rutas, debemos ejecutar el comando route sin parámetros:

Ver rutas
sudo route
Establecer rutas puede ser muy interesante cuando queremos dividir nuestra red en diferentes subredes y disponemos de un servidor con varias tarjetas de red.
