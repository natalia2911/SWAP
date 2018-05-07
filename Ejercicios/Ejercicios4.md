# Ejercicio T4.1:
### Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares.
IBM presentó este jueves una computadora central --'mainframe'-- llamada 'zEnterprise', que según la compañía es la "más potente" fabricada hasta la fecha, con una eficiencia energética superior a las generaciones anteriores. 

Fruto de más de 3 años de trabajo y 1.173 millones de euros (1.500 millones de dólares) de inversión en I+D, IBM ha involucrado a más de 5.000 técnicos y 18 laboratorios de investigación de todo el mundo en su desarrollo. El lanzamiento ha supuesto 31 millones de horas de trabajo.

Hoy en día los servicios de granja web se ofrecen para pequeñas y medianas empresas por meses, los precios oscilan desde los 3 euros a los cien. Después tenemos empresas que ofrecen diseño, instalación, mantenimiento adecuado a cada cliente, por lo que no te dan precio a no ser que contactes con ellos. 
Aun no teniendo un precio comparativo, se ve claramente que el precio del mainframe es infinitamente superior a la granja web.


# Ejercicio T4.2:
### Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros.

#### Cisco SMB RV345-K9-G5 Cisco RV345 Dual WAN Gigabit VPN Router

Precio: 344.99EUR

IVA:72.45

Precio total: 417.43

Product Overview

Small businesses are constantly exposed to Internet threats. The Cisco RV340, RV345, and RV345P Dual WAN Gigabit VPN Routers connect small businesses to the Internet and protect employees from unwanted content and malicious websites without compromising the online experience. The routers help boost employee productivity and overall network performance by limiting Internet surfing to appropriate site categories and eliminating unwanted network traffic. Users are automatically protected from malicious or compromised websites, regardless of site categorization. End devices and applications can be identified and treated according to user-defined policies for improved productivity and optimal network usage.
With an intuitive user interface, the RV340, RV345, and RV345P enable you to be up and running in minutes. These routers provide reliable, highly secure connectivity that is so transparent you will not know it is there.

Features and Benefits

- 2 WAN ports (RJ-45) allow load balancing and resiliency
- 16 LAN ports (RV345) allow for a small device footprint with sufficient ports
- 2 USB ports support a 3G/4G modem or flash drive
- Flexible VPN functionality for secure interconnectivity
- Support for Cisco AnyConnect® Secure Mobility Client, ideal for remote access by mobile devices
- Dynamic web filtering enables business efficiency and security while connecting to the Internet
- Client and application identification allow Internet access policies for end devices and Internet applications to help ensure performance and security

The Cisco RV340, RV345, and RV345P Dual Gigabit WAN VPN Routers are the choice for any small business network that requires performance, security, and reliability.
 

Description Specification

Ports
Ethernet WAN 2 RJ-45 Gigabit Ethernet 16 RJ-45 Gigabit Ethernet (RV345)
Console 1 RJ-45 for future use
USB 2 for external 3G/4G dongle or flash drive
Security
Firewall Stateful packet inspection, 900-Mbps throughput for TCP, User Datagram Protocol (UDP) traffic
Web security and app visibility (licensed
feature)
Dynamic web filtering: Cloud based, more than 80 categories, more than 450 million domains
classified
Application identification: Assign policies to Internet applications
Endpoint identification: Assign policies based on end device category and operating system
VPN
IP Security (IPsec) Yes (50 connections, 650 Mbps throughput)
IPsec site-to-site Preconfigured profiles for Amazon Virtual Cloud and Microsoft Azure
Layer 2 Tunneling Protocol (L2TP) (over
IPsec)
Remote access via L2TP (over IPsec for MS Windows)
IPsec remote access Remote access from standard IPsec client and Cisco IPsec VPN (for example, Mac OS, Apple
iOS clients)
Cisco SSL VPN
(Cisco AnyConnect)
Ideal for mobile devices. Remote access from Cisco AnyConnect Secure Mobility Client. Max 50
connections (2 sessions included, can be upgraded to 50 sessions). Cisco AnyConnect client sol


#### CISCO Gigabit - Router VPN (Dual WAN)
Precio:	EUR 161,82 


- Protocolos de red admitidos: PPTP, L2TP, IPSec, PPPoE, DHCP
- Tecnología de cableado: 10/100 / 1000BASE-T (X)
- Ethernet LAN, velocidad de transferencia de datos: 10, 100, 1000 Mbit / s
- Entrada de corriente de 1A

Detalles técnicos

Marca	Cisco

Series	RV042G

Peso del producto	599 g

Dimensiones del producto	20 x 13 x 3,9 cm

Número de modelo del producto	RV042G-K9-EU

Color	Negro

Tipo de conectividad	No compatible

Número de puertos ethernet	6

Voltaje	12 voltios
 	 
 
Descripción del producto

Rendimiento. Capacidad de la VPN: 75 Mbps. Capacidad. Túneles VPN IPSec: 50. Red / Protocolo de transporte: PPTP L2TP IPSec PPPoE DHCP. Protocolo de direccionamiento: RIP1 RIP2 direccionamiento IP estático. Protocolo de gestión remota: SNMP 1 SNMP 2 SNMP 3 HTTP HTTPS. Algoritmo de cifrado: Triple DES SHA MD5 AES. Protección firewall soporte de NAT soporte para PAT soporte para NAPT Stateful Packet Inspection (SPI) prevención contra ataque de DoS (denegación de servicio) copia de puertos soporte IPv6 pasarela VPN filtrado de URL bloqueo de dominios admite Rapid Spanning Tree Protocol (RSTP) Quality of Service (QoS) Servidor DHCP desví¬o de puertos activación de puertos cliente DHCP. Cumplimiento de normas: IEEE 802.3 IEEE 802.3u IEEE 802.1D IEEE 802.3ab IEEE 802.1p IEEE 802.1x IEEE 802.11e IEEE 802.3az certificado FCC Clase B CTick cUL. Indicadores de estado Estado puerto sistema DMZ DMZ/Internet diagnóstico. Expansión / Conectividad. Interfaces. LAN: 4 x 10BaseT/100BaseTX/1000BaseT RJ45. WAN: 2 x 10BaseT/100BaseTX/1000BaseT RJ45. Alimentación. Dispositivo de alimentación: Transformador eléctrico externo. Medidas y peso. Anchura: 13 cm. Profundidad: 20 cm. Altura: 3.86 cm. Parámetros de entorno. Temperatura mínima de funcionamiento: 0 °C. Temperatura máxima de funcionamiento: 40 °C. Ámbito de humedad de funcionamiento: 10 85% (sin condensación)


# Ejercicio T4.5:
### Probar las diferentes maneras de redirección HTTP. ¿Cuál es adecuada y cuál no lo es para hacer balanceo de carga global? ¿Por qué?
Hay cuatro formas de redireccionamiento HTTP:
1.	Mediante HTML. Ejemplo: 

`<meta http-equiv="refresh" content="10; url=http://www.ejemplo.es/">`

2.	Mediante PHP

`<?php
header("Status: 301 Moved Permanently");
header("Location: http://www.ejemplo.es");
exit;
?>`

3.	Mediante Javascript

`<script>`

`<!--

window.location.replace('http://www.ejemplo.es'); 

//-->`

`</script>`

4.	Mediante Apache/.htaccess

`Redirect 301 / http://www.ejemplo.es/`

El más recomendable es mediante .htaccess, ya que está en el root del servidor, es decir, este archivo es invisible, tienes que activar ciertos filtros en tu cliente FTP para verlos.

