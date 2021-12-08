# Wireguard
Proyecto para crear una vpn en Wireguard en Docker.

![alt text](https://github.com/JuanRodenas/Wireguard/blob/main/wireguard.png)

### INSTALAR DOCKER-COMPOSE.YML DE PIHOLE
Edite las siguientes variables:

Descargar [docker-compose.yml](https://github.com/JuanRodenas/Wireguard/blob/main/docker-compose.yml)

- Cambiar el valor de la variable `PEERS=3` por el número deseado de clientes o indicar los nombres de los clientes separados por comas `PEERS=PEER1, PEER2`.
- Abra el puerto `51820/UDP` en el router, y apúntelo a la IP del servidor donde está ejecutando el contenedor.
- Cambiar el valor de la variable `PEERDNS=1.1.1.1, 1.0.0.1` por las DNS deseadas.

### Lanzar el contenedor
Edite el volumen y cambiar la ruta deseada:
~~~
  volumes:
    - /home/root/wireguard/appdata/config:/config
~~~

### Lanzar el contenedor
~~~
docker-compose -up d
~~~

### Ver el log para ver los códigos QR para los usuarios
~~~
docker logs wireguard
~~~

###  Supervisar el tráfico de un cliente conectado
- Acceder al contenedor:
~~~
docker exec -it wireguard bash
~~~
- Y una vez dentro, ejecutamos:
~~~
wg show
~~~

## Ready!
