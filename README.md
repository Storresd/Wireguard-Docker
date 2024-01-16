### INSTALAR DOCKER COMPOSE
Edite las siguientes variables:

Descargar docker compose <a title="download" href="https://github.com/JuanRodenas/Wireguard/blob/main/docker-compose.yml"><img src="https://github.com/JuanRodenas/Duckdns/blob/main/files/down.png" alt="download" width="100" align="center"/></a>

Simplemente tirando de `lscr.io/linuxserver/wireguard` debería recuperar la imagen correcta para su arco, pero también puede tirar de imágenes específicas de arco a través de etiquetas.

### Versión latest docker Wireguard
![Docker Image Version (latest)](https://img.shields.io/docker/v/linuxserver/wireguard/latest?arch=amd64&color=blue&logo=docker&logoColor=blue&style=for-the-badge)
![GitHub Release Date](https://img.shields.io/github/release-date/linuxserver/docker-wireguard?color=blue&label=Latest%20release&logo=docker&style=for-the-badge)

### Variables del docker-compose
- Cambiar el valor de la variable `PEERS=3` por el número deseado de clientes o indicar los nombres de los clientes separados por comas `PEERS=PEER1, PEER2`.
- Abra el puerto `51820/UDP` en el router, y apúntelo a la IP del servidor donde está ejecutando el contenedor.
- Cambiar el valor de la variable `PEERDNS=1.1.1.1, 1.0.0.1` por las DNS deseadas.
- añada el dominio de acceso en `SERVERURL`.

### Lanzar el contenedor
Edite el volumen y cambiar la ruta deseada:
~~~
  volumes:
    - /patch/to/data/wireguard/appdata/config:/config
~~~

### Lanzar el contenedor
~~~
docker-compose up -d
~~~

### Ver el log para ver los códigos QR para los usuarios
~~~
docker logs wireguard
~~~

### Supervisar el tráfico de un cliente conectado
- Acceder al contenedor:
~~~
docker exec -it wireguard bash
~~~
- Y una vez dentro, ejecutamos:
~~~
wg show
~~~
