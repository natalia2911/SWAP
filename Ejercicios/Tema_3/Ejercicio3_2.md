# Ejercicio T3.2:
### Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes.

#### Linux: 
- Zeroshell puede funcionar tanto como un filtro de paquetes, es decir, el filtrado basado en las condiciones (reglas) situado en la cabecera del paquete, y como Stateful Packet Inspection (SPI) es decir, el filtrado de los paquetes en base a su correlación con las conexiones ya abierto u otros paquetes ya transitado.

- La aplicación de filtrado más utilizada con Linux 2.4 es Netfilter; reemplaza con creces a ípchains', utilizada con los núcleos Linux 2.2. Netfilter tiene dos partes: un componente del núcleo que debe compilarse en el núcleo y el comando íptables' que ya debería estar disponible en su sistema

- Un firewall es un dispositivo, ya sea software o hardware, que filtra todo el tráfico de red. El sistema operativo Linux dispone de un firewall llamado IPtables.

sudo service iptables start //iniciar

sudo service iptables stop //parar

sudo service iptables restart //reiniciar

#### windows

- Plataforma de filtrado de Windows permite o bloquea alguna conexión.
La Plataforma de filtrado de Windows (WFP) permite a los proveedores de software independientes (ISV) filtrar y modificar los paquetes de TCP/IP, supervisar o autorizar conexiones, filtrar tráfico protegido por protocolos de seguridad de internet (IPsec) y filtrar las llamadas a procedimiento remoto (RPC).
