---
layout: post
title: "Abandonando los servicios de Google"
category: Technology
tags:
- privacidad
- google
- mailbox.org
- email
- pgp
---

Desde hace tiempo soy consciente de los problemas de privacidad que tenemos en
Internet donde empresas como Google, Facebook o Amazon pueden conocernos mejor
que nuestros familiares o parejas. Cerré hace tiempo mi cuenta de Facebook. Ya
no uso Dropbox o similares porque monté mi propio servidor Nextcloud. Pero
siempre he sido superdependiente de los servicios de Google (correo
electrónico, agenda, tareas, notas...). Así que hace unos meses empecé a
plantearme ir abandonando Google. Pero todo se ha visto acelerado al seguir
habitualmente el subreddit
[privacytoolsIO](https://www.reddit.com/r/privacytoolsIO/) y al ver el
documental [La línea
tenebrosa](http://www.rtve.es/alacarta/videos/la-noche-tematica/noche-tematica-linea-tenebrosa/5481895/)
en TVE2.

Después de considerar varios proveedores de email proprivacidad de pago
([ProtonMail](https://protonmail.com), [Tutanota](https://www.tutanota.com),
[Posteo](https://posteo.de)...), me he decantado por
[mailbox.org](https://mailbox.org). Por 1€/mes tienes email (2GB), calendario,
tareas, almacenamiento cloud (100MB) y ofimática (editor de texto, hojas de
cálculo y presentaciones). Todo con protocolos estándares (IMAP, SMTP, WebDAV,
CalDAV, CardDAV) y con un soporte de PGP bastante aceptable. Existe hasta la
posibilidad de cifrar todo email entrante y documento alojado en el
almacenamiento cloud con tu clave PGP.

Ya puestos he configurado mi dominio personal (chrpinedo.me) y ahora mi email
personal es christian(at)chrpinedo(dot)me. Con lo que si en un momento dado
decido cambiar otra vez de proveedor de email, ya no tengo por qué cambiar mi
dirección de email.

Junto con este cambio he aprovechado para mejor algunas cosas relacionadas con
la privacidad:

- Reconfigurar [mi clave PGP
  0x9306dfd0cde4b542](http://pgp.mit.edu/pks/lookup?op=vindex&search=0x9306DFD0CDE4B542).
- Cambiar las aplicaciones de mi dispositivo Android priorizando aplicaciones
  FOSS de la tienda de aplicaciones F-Droid:
    - Email: FairEmail
    - PGP: Openkeychain
    - Sincronización CalDAV/CardDAV: Dav5x
    - Calendario: Simple Calendar Pro
    - Tareas: Opentasks

Todavía tengo servicios de Google que uso pero creo que podré ir eliminado poco
a poco. Estoy probando la aplicación Carnet de Nextcloud para reemplazar Google
Tasks. Para Google Photos puedo usar Nextcloud directamente. Y quizás la
aplicación que veo más difícil de reemplazar es Google Maps.

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Si queréis hacerme algún comentario, ya sabéis mi nueva dirección de email y
podéis usar mi clave PGP para tener conversaciones privadas por Internet. Don't
be evil!
-----BEGIN PGP SIGNATURE-----

iQIzBAEBCAAdFiEE2MRvraUAeZibzsnyJDdgzkpuBZIFAl4rWiMACgkQJDdgzkpu
BZJTDw//TKweZRQab5EgWwuiV+K/B/bMRqbUv/OQpYhSUvdYnJ+2PB+txogDkYta
iNXLZ6vVoaxe1Eb0yGYZHLn89rKamT/pzznNVRRt5FNaHxKLJYabhK3liop2sNct
klLOUVcwK3918VqtYEEv/rx/M5auUZuiadYGjuVohHXMBBCUgOBEQJTOQ2ugL0sW
ov8DznjA7RAJf5xUzBz0nXJtsx8Qxu11ofu2VEr0ySXgZDGJBQCG40/KEidiKcRu
7AWriXhvAy+Bzu+7hlXfg8vZLArn7nglf2Wov4efMbZh7i3PbItPabyQiJ7eqUaw
Gw9zd2eqxHCskoTfpa1CnA9wYH4PKBxfG2kSvJGXMJcowhRLwgG/AYmRa7+TAtzR
h+DsPy+WGVeMANbvWY/hz/tmNbzmn2tKMs0fqsG3SnrB95j9lqygf//oxHRkOPL6
or0oyPd97dGnH9D9OfE7I6y/a7ucFSPWFQ34+CS4F9CefyCH+Vo52D6lcmb9vkBb
/jOyKanPgPYXDmpFDTggMGaZTBgSCeBnu7pufgta0OlQ1NoVahTeBcv+Qb3xfYSq
cClQv67B8gtpdaYHKd77sqsrcWnDa7nQGQcFuiAmOGxA03NbtjkDDXCaBrpoZfZT
Ojduv+vmlfB2bMe2xW0W8gEjlTnaHyT9j8BWnoYmfKWkna1hzrw=
=DpIF
-----END PGP SIGNATURE-----
```
