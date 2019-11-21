# Ejercicio T2.2:

### Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad. Como ejemplo, examina ![PM2](https://github.com/Unitech/pm2) que sirve para administrar clústeres de NodeJS.

Lo primero, vamos a ver que es NodeJS:

NodeJS proporciona una manera fácil para construir programas de red escalables, es decir, cuando tenemos un servidor y el cuello de botella de toda la arquitectura de aplicación Web es el número máximo de conexiones concurrentes que puede manejar el servidor, resuelve este problema cambiando la forma en que se realiza una conexión con el servidor, en lugar de generar un nuevo hilo para cada conexión, cada conexión dispara una ejecución de evento dentro del proceso del motor de NodeJS( usa un modelo de programación orientado por eventos), de esta forma nunca se quedará en punto muerto porque no bloquea directamente para llamadas E/S, en definitiva, soportará decenas de miles de conexiones concurrentemente.
	
Node no es un programa de servidor, sino que tiene módulos que se pueden agregar a su núcleo mismo. Ejecuta V8 JavaScript del lado del servidor, V8 JavaScript es el motor subyacente que Google usa con su navegador Chrome, creó un intérprete ultra-rápido escrito en c++, se puede incorporar a cualquier aplicación que desee, así que Node usa el motor V8 JavaScript escrito por Google y le da otro propósito para usarlo en el servidor.
	
Por todo lo expuesto, se usa para situaciones en que nuestro servidor esté esperando una gran cantidad de tráfico y antes de responder al cliente no requiramos un procesamiento muy grande. ¡[enlace](https://www.ibm.com)

PM2 es un gestor de procesos que se usa para ejecutar una aplicación NodeJS como proceso de manera perpetua en el servidor en producción. Esto da solución al problema de que ante el error de tu aplicación el servidor quedará caído, también al reinicio del servidor se necesitaría volver a arrancar los procesos manualmente. 
	
Para comenzar a usar MP2 podemos ver la pagina ¡[mp2]( http://pm2.keymetrics.io/). En conclusión, tendremos una librería gratuita, capaz de aguantar enormes cantidades de volumen de trafico con un consumo de recursos muy reducido y con herramientas que permiten realizar la monitorización de las aplicaciones de manera remota. ![desarrolloweb](https://desarrolloweb.com)
	
El modo de clúster permite escalar las aplicaciones a través de todas las CPU disponibles, sin modificaciones de código. Esto aumenta enormemente el rendimiento y la confiabilidad de sus aplicaciones, dependiendo de la cantidad de CPU disponibles.

También hemos encontrado Microsoft BizTalk Server, servidor de alta disponibilidad de Microsoft, este usa la aplicación Microsoft Operations Framework (MOF), la cual ofrece una administración fácil de los diferentes servicios TI, teniendo du propia biblioteca TechNet. Dejamos un enlace a su página principal ![microsoft](https://msdn.microsoft.com).


# Ejercicio T2.3:
### ¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor? Buscar herramientas y aprender a usarlas...¡o recordar cómo usarlas!

**Tenemos herramientas cómo:**

- Nagios es un programa de monitoreo de host/servicio/red.
- Munin es una herramienta de monitoreo de recursos en red que analiza el rendimiento
- Ganglia es un sistema de monitoreo distribuido y escalable para sistemas informáticos de alto rendimiento como por ejemplo clústeres.
- Zabbix es una herramienta de monitoreo de varias redes, así como del registro del estado de los servicios en red. Lo hemos usado en alguna práctica.
- Jetstress 2010 de Exchange Server ![technet](https://technet.microsoft.com) , herramienta para la evaluación de la escalabilidad y el rendimiento de nuestro sistema, se hacen las pruebas antes de colocar los datos en producción en el servidor, está diseñado para entornos de prueba.


# Ejercicio T2.4:
### Buscar ejemplos de balanceadores software y hardware (productos comerciales).
Como balanceadores hardware vamos a nombrar:

- Servidores Dell, ejemplo modelo Dell PowerEdge R430, ofrecido por la empresa hostalia como servidor hardware de alto rendimiento ¡[hostalia](https://www.hostalia.com/dedicados/?gclid=EAIaIQobChMI3bqE3fD62QIVEpIYCh0TUwucEAAYASAAEgIU0fD_BwE)
- Servidores dedicados de la empresa OVH, como SP-32, Host-64L, Mc-64-OC ¡[ovh]( https://www.ovh.es/servidores_dedicados/)

Balanceador software hay muchos, Nginx o Haproxy que hemos usado en la practica 3, Cisco Ace, CISCO IOS (si tenemos un router CISCO, tenemos un balanceador) , Coyote Point, Barracuda (incluye prevención de intrusiones), Zen Load Balancer, etc.
### Buscar productos comerciales para servidores de aplicaciones.
Servidores de aplicación Java como Weblogic de Oracle, JBoss Enterprise Application Platform de Red Hat, WebSphere de IBM.

Servidores de aplicaciones en la nube de la empres 1&1 ¡[1&1]( https://www.1and1.es/cloud-app-center/aplicaciones-cloud)
### Buscar productos comerciales para servidores de almacenamiento.
Empresa OVH  ofrece servidores de almacenamiento como FS-12T, FS-30T, FS-MAX  ¡[ovh](https://www.ovh.es/servidores_dedicados/storage/)
