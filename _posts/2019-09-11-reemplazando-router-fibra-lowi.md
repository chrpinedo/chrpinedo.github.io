---
layout: post
title: "Y ahora reemplazando el router de fibra de Lowi"
category: Technology
tags:
- router
- fibra
- mikrotik
- openwrt
- lowi
---

Casualidades de la vida, después de estar años con Movistar y Tuenti, me
molesto en cambiar el router por uno propio y al de poco me paso a Lowi. Así,
que he tenido que investigar ahora como reemplazar el router que pone Lowi (en
realidad los técnicos de Vodafone).

Afortunadamente todo la información de cómo cambiar el router de Lowi está en
los foros de
[bandaancha.eu](https://bandaancha.eu/foros/cambiar-router-lowi-h-500-s-otro-1729084).

Lowi proporciona dos equipos: una ONT de GPON y un router ethernet (también
llamado neutro). Lo que he hecho es dejar la ONT de Lowi y cambiar el router
por mi router Mikrotik. Para configurar nuestro router necesitamos saber las
credenciales de PPPoE y la VLAN a usar. 

La VLAN a usar en caso de usar fibra indirecta de Movistar es el VLANID 24.

El tema de las credenciales PPPoE es un poco más complicado ya que Lowi no las
debe querer proporcionar. El proceso que hay que seguir es el indicado en el
foro de bandaancha.eu:
1. Desconectar el cable de red de la boca WAN que une a la ONT.
2. Resetear el router de Lowi pulsando el botón reset durante 11 segundos.
3. Conectar un portatil a la boca LAN1 del router de Lowi
4. Conectarnos a la web de administración del router Lowi en
   https://192.168.0.1 con el usuario admin y la contraseña l033i-h500s.
5. Ir a "estado y soporte" y "port mirroring".
6. Activar el "port mirroring" con las opciones "-i ppp1".
7. Ahora en el portatil conectado a la boca LAN1 del router Lowi arrancamos un
   wireshark y empezamos a capturar el tráfico.
8. Conectamos la boca WAN a la ONT para que se establezca la conexión de
   Internet.
9. Capturamos el tráfico con wireshark durante 2 o 5 minutos hasta que la
   conexión a Internet funcione.
10. En la captura de wireshark filtramos solo el tráfico "http" y buscamos
    dentro de esos paquetes IP la cadena de texto "@lowi" para encontrar el
    usuario y la contraseña de PPPoE que estábamos buscando.

Y con esto ya tenemos todos los datos para reemplazar el router de Lowi,
dejando la ONT que nos han traido.
