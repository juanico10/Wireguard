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


## COMPROBAR SEGURIDAD VPN
Una forma de comprobar si tu VPN está cifrando tu tráfico es verificando la configuración de seguridad de tu conexión VPN. puede usar herramientas en línea para verificar si su conexión VPN está cifrando su tráfico de forma efectiva. Hay varias herramientas en línea que pueden hacer esta comprobación:

Recomendamos: Una política estrictamente sin registros, sin ningún registro de actividad o conexión.	

### Comprueba si tienes filtraciones en tu IP
<details>
<summary>¿Cómo comprobar si tu IP se está filtrando?</summary>

La IP es tu dirección en internet y, probablemente, el dato privado más importante que debes proteger a la hora de navegar por la red. Tu IP puede desvelar el lugar geográfico donde te encuentras y las páginas web que visitas, así que es muy importante que la mantengas protegida en todo momento.

1. Desactiva tu VPN y accede a una de las páginas indicadas para descubrir cuál es tu IP real.
2. Anota tu IP.
3. Activa tu VPN y realiza el test de nuevo. Si tu IP sigue siendo la misma, tu VPN no está funcionando adecuadamente.

<Original>&nbsp;¿Cómo comprobar si tu IP se está filtrando?</Original>

&nbsp;
<p>  &nbsp;&nbsp;[dnsleaktest](https://www.dnsleaktest.com/): Este sitio web te permite verificar si tu VPN ha enrutado correctamente todo tu tráfico a través de la conexión VPN. También te muestra detalles sobre los servidores DNS a los que estás conectado.</p>
<p>  &nbsp;&nbsp;[ipleak](https://ipleak.net/): Este sitio web te permite comprobar la dirección IP que se está mostrando para tu conexión, asegurándote de que corresponde a la dirección IP del servidor VPN al que estás conectado.</p>
<p>  &nbsp;&nbsp;[perfect-privacy](https://www.perfect-privacy.com/check-ip/): Esta herramienta te permite verificar si tu dirección IP y tu ubicación geográfica coinciden con la dirección IP y la ubicación del servidor VPN al que estás conectado.</p>
<p>  &nbsp;&nbsp;[do-i-leak](https://www.top10vpn.com/tools/do-i-leak/): Realiza pruebas para verificar la seguridad de tu conexión VPN y detecta posibles fugas.</p>
<p>  &nbsp;&nbsp;[ExpressVPN Leak Testing Tools](https://github.com/expressvpn/expressvpn_leak_testing) Ofrece un conjunto de herramientas en línea para realizar pruebas y comprobar la seguridad de tu conexión VPN.</p>
<p>  &nbsp;&nbsp;[fugas-ip-test](https://www.top10vpn.com/es/herramientas/fugas-ip-test/) Es capaz de identificar fugas de IP, DNS, WebRTC y geolocalización, además de fugas de IP y DNS al descargar torrents.</p>

</details>
&nbsp;

### Herramienta de prueba de Kill Switch
La función de un Kill Switch en una VPN es simplemente parar la conexión. En cuanto hay un problema, sea cual sea, y la VPN deja de funcionar correctamente, esta característica evitaría que sigamos conectados a Internet. Básicamente actúa como un interruptor de seguridad. Un botón automático que se activa en cuanto la VPN se desconecta.

<details>
<summary>¿Cómo comprobar prueba de Kill Switch?</summary>

<Original>&nbsp;Page to check your selfhosted from fivefilters</Original>

<p>  &nbsp;&nbsp;[dnsleaktest](https://www.dnsleaktest.com/): Este sitio web te permite verificar si tu VPN ha enrutado correctamente todo tu tráfico a través de la conexión VPN.</p>
<p>  &nbsp;&nbsp;[kill-switch](https://www.top10vpn.com/es/guias/kill-switch-vpn/) Nos permite verificar si hay fugas de IP al cambiar los servidores VPN o en caso de que Internet se desconecte de forma inesperada. Un buen Kill Switch de VPN debería poder prevenir todas las fugas y pasar nuestras pruebas.</p>

</details>
&nbsp;



### Comprueba si tienes filtraciones en tu DNS
En ocasiones, incluso si tu IP está protegida, tu DNS puede desvelar tu ubicación. El DNS se encarga de transcribir las direcciones textuales de las webs en términos numéricos, es decir, en IPs. Si tu equipo no está convenientemente protegido, este proceso de conversión puede desvelar tu ubicación y las webs que has visitado. La exposición de tu DNS, además, puede hacerte vulnerable a ataques de secuestro de DNS o ‘DNS hijacking’.

<details>
<summary>¿Cómo comprobar si tu DNS está filtrando tu IP?</summary>

<Original>&nbsp;Comprueba si tienes filtraciones en tu DNS</Original>
1. Recuerda tu IP del apartado anterior.
2. Accede a esta página para comprobar si tu IP se filtra a través de tu DNS.
3. Si reconoces tu IP, tienes una filtración en tu DNS.
4. Si tu IP no aparece en primera instancia, puedes usar el test extendido para asegurarte de que no haya filtraciones.


<p>  &nbsp;&nbsp;[fugas-ip-test](https://www.top10vpn.com/es/herramientas/fugas-ip-test/)</p>
<p>  &nbsp;&nbsp;[test-ipv6.com](http://www.test-ipv6.com/)</p>
<p>  &nbsp;&nbsp;[checkip.amazonaws.com](http://checkip.amazonaws.com/)</p>
<p>  &nbsp;&nbsp;[ipaddress.com](https://www.ipaddress.com/)</p>

</details>
&nbsp;

### Comprueba si tienes filtraciones en tu WebRTC
El WebRTC es un sistema de comunicación integrado en la mayoría de navegadores como Firefox, Opera, Chrome y Brave. Está diseñado para facilitar el intercambio de audio y video en tiempo real entre usuarios mediante el establecimiento de una conexión directa entre ellos, pero presenta vulnerabilidades que pueden filtrar las IPs de sus usuarios.

<details>
<summary>¿Cómo comprobar si tu WebRTC está filtrando tu IP?</summary>

<Original>&nbsp;Comprueba si tienes filtraciones en tu WebRTC</Original>

1. Anota tu IP original como hemos visto en los apartados anteriores.
2. Activa tu VPN y dirígete a la página siguiente.
3. Si reconoces tu IP bajo la categoría ‘Your IP addresses – WebRTC detection’, tu WebRTC está filtrando tu IP.

<p>  &nbsp;&nbsp;[webrtc](https://browserleaks.com/webrtc)</p>
<p>  &nbsp;&nbsp;[Browser Privacy](https://tenta.com/test/) </p>
<p>  &nbsp;&nbsp;[Cloudflare Browser Check](https://www.cloudflare.com/es-es/ssl/encrypted-sni/) </p>
<p>  &nbsp;&nbsp;[Cover Your Tracks](https://coveryourtracks.eff.org/) </p>

Cómo solucionarlo
1. Usar un navegador que no tenga WebRTC. Tienes una lista [aquí](https://en.wikipedia.org/wiki/WebRTC).
2. Desactivar el WebRTC de tu navegador siguiendo estos pasos: [link](Cómo solucionarlo).
3. Instalar extensiones en tu navegador que limiten el acceso a tu WebRTC. Si utilizas Google Chrome, te servirá la extensión WebRTC Network Limiter.
</details>
&nbsp;

### Herramientas de pruebas de velocidad
Utilizamos dos herramientas para probar las velocidades de VPN.

<details>
<summary>¿Cómo comprobar si tu WebRTC está filtrando tu IP?</summary>
Controla tu conexión para poder decirte las velocidades de descarga y subida, además del tiempo ping. Utilizamos esto para saber la diferencia entre las velocidades de nuestra conexión a Internet con y sin una VPN.

<Original>&nbsp;Page to check your vpn</Original>

<p>  &nbsp;&nbsp;[speedtest.net](http://speedtest.net/) </p>
<p>  &nbsp;&nbsp;[prueba-velocidad-vpn](https://www.top10vpn.com/es/herramientas/prueba-velocidad-vpn/) </p>
<p>  &nbsp;&nbsp;[openspeedtest](https://openspeedtest.com/) </p>
<p>  &nbsp;&nbsp;[fast.com](https://fast.com/es/) </p>
<p>  &nbsp;&nbsp;[speedsmart.net](https://speedsmart.net/) </p>

</details>
&nbsp;


## 🎉 ¡Ready!














### Check your SelfHosted:

<details>
<summary>fivefilters:</summary>

<Original>&nbsp;Page to check your selfhosted from fivefilters</Original>

<p>  &nbsp;&nbsp;https://blockads.fivefilters.org/</p>
</details>
&nbsp;