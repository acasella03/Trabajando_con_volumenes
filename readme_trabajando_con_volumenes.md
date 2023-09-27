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
2. Crea un contenedor con el nombre 'dam_web1'.
3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?
4. Utiliza bind mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.
    - Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/
5. Realiza un 'hola mundo' en html (usa Code) y comprueba que accedes desde el navegador.
6. Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.
7. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:
    - http://localhost:9080 
    - http://localhost:8000
8. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página

## Respuesta:
### 1.
- [x] Descarga la imagen 'httpd' y comprueba que está en tu equipo.
```
Comando:
            $ docker pull httpd
```
> [!NOTE]
> Este comando descargará la última versión de la imagen 'httpd' desde el registro público de Docker y la almacenará en tu sistema local.

### 2.
- [x] Crea un contenedor con el nombre 'dam_web1'.
```
Comando:
            $ docker run -d --name dam_web1 httpd
```
> [!NOTE]
>Una vez ejecutado este comando, se creará un nuevo contenedor llamado 'dam_web1' basado en la imagen 'httpd'. Este contenedor ejecutará el servidor web Apache contenido en la imagen y estará en segundo plano. Puedes acceder al servidor web dentro del contenedor a través del puerto 80 del contenedor.

### 3.
- [x] Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?
```
Comando:
            $ docker run -d --name dam_web1 -p 8080:80 httpd:2.4
```
> [!NOTE]
>Para poder acceder al servidor web Apache que se encuentra dentro del contenedor 'dam_web1' desde el navegador de mi equipo, debo realizar un mapeo de puertos para redirigir el tráfico desde un puerto en mi máquina local al puerto 80 del contenedor. Esto permite acceder al servidor web Apache en el contenedor desde el navegador web en mi máquina local utilizando la dirección http://localhost:8080.

> [!IMPORTANT] 
> Si ya tengo un contenedor debo eliminarlo para poder ejecutar éste comando con su mapeo y con la versión 2.4. 

### 4 y 5.
- [x] Utiliza bind mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.
    - Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/
- [x] Realiza un 'hola mundo' en html (usa Code) y comprueba que accedes desde el navegador.
```
Comando:
            $ docker run -dit --name dam_web1 -p 8080:80 -v /home/dam2/Documentos/Apache/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
```
> [!NOTE]
> El comando crea un nuevo contenedor Docker a partir de la imagen httpd que ejecuta un servidor web Apache. El contenedor se ejecuta en segundo plano, se llama "dam_web1" y se realiza un mapeo de puertos para permitir que el puerto 8080 de mi máquina local se comunique con el puerto 80 del contenedor. Esto permite acceder al servidor web Apache en el contenedor desde tu navegador web en tu máquina local utilizando la dirección http://localhost:8080.

> [!IMPORTANT] 
> Si ya tengo un contenedor debo eliminarlo para poder ejecutar éste comando con su mapeo y con la versión 2.4. 

### 6 y 7.
- [x] Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.
- [x]  Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:
    - http://localhost:9080 
    - http://localhost:8080
```
Comando:
            $ docker run -dit --name dam_web2 -p 9080:80 -v /home/dam2/Documentos/Apache/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
```
> [!IMPORTANT]
> Efectivamente en cada servidor funciona el mismo mensaje en el navegador cuando se hacen las dos consultas

![imagen1](https://github.com/acasella03/Trabajando_con_volumenes/blob/main/images/localhost_9080.png)
![imagen2](https://github.com/acasella03/Trabajando_con_volumenes/blob/main/images/localhost_8080.png)

### 8.
- [x] Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página

Colocando el el buscador web:

        http://10.0.9.17:9080/
        http://10.0.9.17:8080/

Veo que efectivamente se realizan los cambio en ambos servidores.