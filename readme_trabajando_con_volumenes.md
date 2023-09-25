# Tarea: trabajando con volumenes

## Mapeo de puertos

En el contexto de un servidor web Apache, el mapeo de puertos se refiere a la
configuración que permite a Apache escuchar en un puerto específico en una dirección IP o en todas las interfaces de red disponibles. 
Esto es fundamental para que el servidor web pueda recibir solicitudes de clientes web 
(navegadores, aplicaciones, etc.) y responder a ellas.

Se hace con el comando:
```
$ docker run -dit --name dam_apache-app -p 8080:80 httpd:2.4
```
> [!IMPORTANT]
> Este comando ejecuta un contenedor Docker basado en la imagen oficial de Apache HTTP Server versión 2.4. El contenedor se ejecuta en segundo plano, se llama "dam_apache-app", y el puerto 8080 del sistema host se redirige al puerto 80 del contenedor, lo que permite acceder al servidor web Apache dentro del contenedor desde el sistema host a través del puerto 8080.

## Enunciado:
Utilizaremos la imagen de Apache. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones:

1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.
2. Crea un contenedor con el nombre 'dam_httpd'.
3. Mapea el puerto 80 del contenedor con el puerto 8000 de tu máquina.
4. Utiliza bind mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.<br>
Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/
5. Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador.
6. Crea un volumen para este mismo fin.
7. Crea un contenedor 'dam_web1' que use este volumen para el 'htdocs'
8. Utiliza Code para hacer un hola mundo en html
9.  Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.
10. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:<br>
http://localhost:9080<br>
http://localhost:8000
11.  Tienen que salir la misma página web

## Respuesta:
### 1 y 2.
- [x] Descarga la imagen 'httpd' y comprueba que está en tu equipo.
- [x] Crea un contenedor con el nombre 'dam_httpd'.
```
Comando:
            $ docker run -dit --name dam_httpd -p 8080:80 httpd:2.4
```
> [!NOTE]
> Este comando ejecuta un contenedor Docker basado en la imagen oficial de Apache HTTP Server versión 2.4. El contenedor se ejecuta en segundo plano, se llama "dam_apache-app", y el puerto 8080 del sistema host se redirige al puerto 80 del contenedor, lo que permite acceder al servidor web Apache dentro del contenedor desde el sistema host a través del puerto 8080.