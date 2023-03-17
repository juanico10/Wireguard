# Wireguard
Proyecto para crear una vpn en Wireguard en Docker.

![alt text](https://github.com/JuanRodenas/Wireguard/blob/main/assets/wireguard.png)

### INSTALAR DOCKER-COMPOSE.YML DE WIREGUARD
Edite las siguientes variables:

Descargar docker compose <a title="download" href="https://github.com/JuanRodenas/Wireguard/blob/main/docker-compose.yml"><img src="https://github.com/JuanRodenas/Duckdns/blob/main/files/down.png" alt="download" width="100" align="center"/></a>

Simplemente tirando de `lscr.io/linuxserver/wireguard` debería recuperar la imagen correcta para su arco, pero también puede tirar de imágenes específicas de arco a través de etiquetas.

#### Las arquitecturas soportadas por esta imagen son:

| Architecture | Tag |
| :----: | --- |
| x86-64 | amd64-latest |
| arm64 | arm64v8-latest |

### Versión latest docker Wireguard
![Docker Image Version (latest)](https://img.shields.io/docker/v/linuxserver/wireguard/latest?arch=amd64&color=blue&logo=docker&logoColor=blue&style=for-the-badge)

### Variables del docker-compose
- Cambiar el valor de la variable `PEERS=3` por el número deseado de clientes o indicar los nombres de los clientes separados por comas `PEERS=PEER1, PEER2`.
- Abra el puerto `51820/UDP` en el router, y apúntelo a la IP del servidor donde está ejecutando el contenedor.
- Cambiar el valor de la variable `PEERDNS=1.1.1.1, 1.0.0.1` por las DNS deseadas.

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

## Generador de configuración Wireguard
Esta herramienta es para ayudar con la creación de archivos de configuración para una configuración de WireGuard 'road-warrior' en la que tiene un servidor y un montón de clientes. Simplemente ingrese los parámetros para su configuración particular y haga clic en Generar configuración para comenzar. 
- Web wireguardconfig.com
<p><ul><a href="https://www.wireguardconfig.com/" target="_blank" rel="noopener noreferrer"><img src="https://github.com/JuanRodenas/Wireguard/blob/main/assets/site.png" width="60px"></a></ul></p>

- Web dbca-wa.github.io
<p><ul><a href="https://dbca-wa.github.io/wg-webcfg/wg-webcfg.html" target="_blank" rel="noopener noreferrer"><img src="https://github.com/JuanRodenas/Wireguard/blob/main/assets/site.png" width="60px"></a></ul></p>

## Download App

### Aplicacion android
<ul><a href="https://play.google.com/store/apps/details?id=com.wireguard.android" target="_blank" rel="noopener noreferrer"><img src="https://github.com/JuanRodenas/Wireguard/blob/main/assets/google-play.png" width="60px"></a></ul>

### Aplicacion iPhone/iPad
<ul><a href="https://apps.apple.com/es/app/wireguard/id1441195209" target="_blank" rel="noopener noreferrer"><img src="https://github.com/JuanRodenas/Wireguard/blob/main/assets/app-store.png" width="60px"></a></ul>

## Otro wireguard con GUI
https://github.com/weejewel/wg-easy

## 🎉 ¡Ready!
