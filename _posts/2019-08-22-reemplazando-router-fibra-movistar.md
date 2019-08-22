---
layout: post
title: "Reemplazando el router de fibra de Movistar (o Tuenti)"
category: Technology
tags:
- router
- fibra
- mikrotik
- openwrt
---

Tener un router propio en lugar del típico router que te proporciona el
proveedor de Internet puede tener una serie de ventajas para los que queremos
exprimir la conexión de Internet, por ejemplo, para mejorar la cobertura de
WiFi con un router con más antenas y potencia, mejorar la velocidad del WiFi
con un router que soporte los últimos estándares WiFi AC, tener servicios
avanzados en el router (VPN, proxys, DNSCrypt...) o simplemente tener un
control total sobre el router.  

Antes de tener fibra en casa, con el ADSL, ya tenía un router propio en lugar
del router del proveedor de servicios: utilizaba un modem ADSL conectado a un
router con todas las bocas de red RJ45 Ethernet (a veces también llamado router
neutro) de la marca Mikrotik RB751G-2HnD. En el router corría el software de
Mikrotik RouterOS que permitía hacer virguerías.

Para hacer lo mismo con la fibra de Tuenti y reemplazar el router de Movistar
lo primero que hice fue adquirir el Bridge GPON Huawei HG8310M en
[AliExpress](https://es.aliexpress.com/item/32804227179.html). Este equipo GPON
ONT tiene una interfaz SC a la que conectar la fibra de Tuenti/Movistar y un
puerto 1Gbps al que conectaremos el router Ethernet que tengamos. La
configuración de este dispositivo es muy sencilla y lo único que debemos saber
es la contraseña de GPON que tenía el router viejo de Movistar, que la podemos
sacar navegando por la configuración avanzada del router de Movistar. Si la
conexión de GPON se establece correctamente, el LED de PON debe permanecer
encendido en verde y el el LED de LOS apagado.

El router que he utilizado conectado al ONT es mi viejo router Mikrotik
RB751G-2HnD al que le he cargado el firmware
[OpenWRT](https://www.openwrt.org), que es un firmware libre basado en
GNU/Linux que esta disponible para muchas marcas y modelos de routers. He
decidido dar el salto de RouterOS de Mikrotik a OpenWRT porque lo que tengo
decidido es que mi próximo router soportará OpenWRT pero no será necesariamente
un Mikrotik. Al usar este router en lugar del de Movistar he mejorado
considerablemente la cobertura WiFi de mi casa aunque al ser un router WiFi N
no consigo alcanzar por WiFi los 100Mbps de mi conexión a Internet, así que a
futuro lo cambiaré por un router con WiFi AC (que soporte OpenWRT obviamente).

Para terminar hace falta configurar el router:
1. Conectar el cable de red Ethernet entre la boca WAN del router y la única
   boca de red Ethernet de la ONT.
2. Configurar la VLAN número 6, ya que el tráfico de Internet en la fibra de
   Movistar se manda "tagueado" con el VLAN ID 6. Para ello en nuestro router
   con firmware OpenWRT creamos una nueva VLAN 6 que es "tagueada" en la
   interfaz de WAN y CPU, y "off" en las interfaces de LAN.
3. Crear la interfaz de red de PPPoE. Al crear esta interfaz de red le
   asignaremos la VLAN ID 6 anteriormente creada y las credenciales de
   autenticación son:
   - usuario: adslppp@telefonicanetpa
   - contraseña: adslppp

Si todo ha ido bien, veremos como la interfaz PPPoE levanta y obtiene una
dirección IPv4 pública.
