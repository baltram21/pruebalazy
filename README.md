#Paso 1: Se realiza un escaneo de puertos con Nmap para identificar los servicios activos en la máquina. Esto permite conocer qué puertos están abiertos y qué servicios se están ejecutando en ellos. El comando utilizado es nmap -sC -sV -Pn -T4 10.10.149.79.

Paso 2: Al detectar que hay un servicio HTTP en funcionamiento, se accede a la dirección IP a través del navegador web para explorar la página y analizar su contenido. La dirección ingresada es http://10.10.149.79.

Paso 3: Se inspecciona el código fuente HTML de la página en busca de pistas que puedan revelar información útil, como comentarios, rutas ocultas o referencias a archivos importantes.

Paso 4: Durante la exploración, se detecta una cookie inusual. Al analizar su contenido, se descubre que podría estar revelando la existencia de un directorio dentro del servidor.

Paso 5: Se emplea la herramienta Gobuster para realizar una enumeración de directorios ocultos en el servidor web. Esto permite descubrir rutas que no están enlazadas directamente en la página. El comando utilizado es gobuster dir -u http://10.10.149.79 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt.

Paso 6: Como resultado de la exploración, se identifica una URL alternativa. En lugar del directorio esperado /content, se encuentra otro llamado /imagen, lo que sugiere que podría haber información relevante en esta nueva ubicación.

Paso 7: Se accede al directorio /content/images y se encuentran varios archivos almacenados en él. Entre ellos, destaca un archivo con extensión .xls, el cual contiene fragmentos de código web que podrían ser útiles para la investigación.

Paso 8: Se encuentra un archivo XML en el sistema, pero es importante no ejecutarlo bajo ninguna circunstancia. Se identifica que este archivo es una trampa y podría comprometer el acceso o causar un comportamiento no deseado en la máquina.

Paso 9: Se continúa investigando en busca de más archivos en la página. Como resultado, se localiza un dominio que contiene archivos con extensión .php y .sql, los cuales pueden ser clave para el acceso a la base de datos del sistema.

Paso 10: Dentro de los archivos encontrados, se identifica un archivo con extensión .inc, el cual contiene información relevante como registros de actividad (logs), rutas de directorios adicionales y otros archivos que pueden proporcionar más pistas.

Paso 11: Se localiza una copia de seguridad de la base de datos. Al examinar su contenido, se confirma la existencia de credenciales de acceso con un usuario y una contraseña correctos.

Paso 12: Dentro de la base de datos, se encuentra un código hash que oculta una contraseña. Se procede a desencriptarlo utilizando herramientas especializadas para obtener la contraseña en texto plano.

Paso 13: Se prueban distintas combinaciones de usuario y contraseña hasta dar con una válida. Se descubre que el usuario Manager con la contraseña Password123 permite acceder al sistema con éxito.

Paso 14: Para completar el análisis de seguridad, se utiliza la herramienta Metasploit con el objetivo de realizar un escaneo detallado de la aplicación y detectar posibles vulnerabilidades o exploits que puedan ser aprovechados para obtener un mayor control sobre el sistema.