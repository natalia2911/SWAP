# Ejercicio T2.2:

### Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad. Como ejemplo, examina PM2 ![enlace](https://github.com/Unitech/pm2) que sirve para administrar clústeres de NodeJS.

Lo primero, vamos a ver que es NodeJS:

NodeJS proporciona una manera fácil para construir programas de red escalables, es decir, cuando tenemos un servidor y el cuello de botella de toda la arquitectura de aplicación Web es el número máximo de conexiones concurrentes que puede manejar el servidor, resuelve este problema cambiando la forma en que se realiza una conexión con el servidor, en lugar de generar un nuevo hilo para cada conexión, cada conexión dispara una ejecución de evento dentro del proceso del motor de NodeJS( usa un modelo de programación orientado por eventos), de esta forma nunca se quedará en punto muerto porque no bloquea directamente para llamadas E/S, en definitiva, soportará decenas de miles de conexiones concurrentemente.
	
Node no es un programa de servidor, sino que tiene módulos que se pueden agregar a su núcleo mismo. Ejecuta V8 JavaScript del lado del servidor, V8 JavaScript es el motor subyacente que Google usa con su navegador Chrome, creó un intérprete ultra-rápido escrito en c++, se puede incorporar a cualquier aplicación que desee, así que Node usa el motor V8 JavaScript escrito por Google y le da otro propósito para usarlo en el servidor.
	
Por todo lo expuesto, se usa para situaciones en que nuestro servidor esté esperando una gran cantidad de tráfico y antes de responder al cliente no requiramos un procesamiento muy grande. ¡[enlace](https://www.ibm.com)

PM2 es un gestor de procesos que se usa para ejecutar una aplicación NodeJS como proceso de manera perpetua en el servidor en producción. Esto da solución al problema de que ante el error de tu aplicación el servidor quedará caído, también al reinicio del servidor se necesitaría volver a arrancar los procesos manualmente. 
	
Para comenzar a usar MP2 podemos ver la pagina ¡[mp2]( http://pm2.keymetrics.io/). En conclusión, tendremos una librería gratuita, capaz de aguantar enormes cantidades de volumen de trafico con un consumo de recursos muy reducido y con herramientas que permiten realizar la monitorización de las aplicaciones de manera remota. ![desarrolloweb](https://desarrolloweb.com)
	
El modo de clúster permite escalar las aplicaciones a través de todas las CPU disponibles, sin modificaciones de código. Esto aumenta enormemente el rendimiento y la confiabilidad de sus aplicaciones, dependiendo de la cantidad de CPU disponibles.

También hemos encontrado Microsoft BizTalk Server, servidor de alta disponibilidad de Microsoft, este usa la aplicación Microsoft Operations Framework (MOF), la cual ofrece una administración fácil de los diferentes servicios TI, teniendo du propia biblioteca TechNet. Dejamos un enlace a su página principal ![microsoft](https://msdn.microsoft.com).