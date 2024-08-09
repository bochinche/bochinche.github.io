---
layout: post
title:  "Guía para Comunicarse de Forma Segura en Venezuela: Opciones de Mensajería y VPNs para Evadir la Censura"
date:   2024-08-08 12:00:00 +0100
categories: internet venezuela bloqueo x twitter signal
---

## Resumen rápido (para quien no quiera leer mucho)!

|  Función  |                                                                                                      iOS Apps (Apple)                                                                                                      |                                                                                                                                   Android Apps(google)                                                                                                                                   |
| :-------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Mesajería |                                                                        [Signal](https://apps.apple.com/us/app/signal-private-messenger/id874139669)                                                                        |                                                                                                    [Signal](https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms)                                                                                                    |
|    VPN    | [Tor Browser](https://apps.apple.com/us/app/onion-browser/id519296448) [Tor Cliente VPN](https://apps.apple.com/us/app/orbot/id1609461599), [ProtonVPN](https://apps.apple.com/us/app/proton-vpn-fast-secure/id1437005085) | [Tor](https://play.google.com/store/apps/details?id=org.torproject.torbrowser), [ProtonVPN](https://f-droid.org/en/packages/ch.protonvpn.android/), [CalyxVPN](https://f-droid.org/en/packages/org.calyxinstitute.vpn/), [RiseupVPN](https://f-droid.org/en/packages/se.leap.riseupvpn/) |

Nota: aquí va un [enlace](https://support.signal.org/hc/en-us/articles/360056052052-Proxy-Support) sobre cómo conseguir y utilizar los proxies para Signal y evitar los bloqueos en Venezuela. Enlace en inglés. 

## Contexto

Venezuela atraviesa tiempos complicados desde las elecciones presidenciales de 2024. En medio de la creciente censura y limitaciones al acceso a la información, es crucial entender cómo proteger nuestra capacidad de comunicarnos de manera segura y efectiva. 

### Restricciones y Medidas Recientes

Diversas medidas que limitan la libre expresión han sido impuestas, generando preocupación entre la población. Entre las más destacadas se encuentran:

- **WhatsApp bajo la mira**: Nicolás Maduro ha instado a la población a dejar de usar WhatsApp, promoviendo en su lugar aplicaciones como Telegram y WeChat. [Ver anuncio](https://youtu.be/qO4FYZa-Fu4).

- **Bloqueo de X (ex Twitter)**: Nicolás Maduro anunció un bloqueo temporal de X, ex [Twitter](https://x.com/) por 10 días. Según el observatorio [Netblocks](https://netblocks.org/), este bloqueo ya es visible. [Más detalles](https://mastodon.social/@netblocks/112929340515361487).

- **Signal también afectada**: Netblocks reporta que Signal, otra aplicación de mensajería, está siendo bloqueada en Venezuela. [Ver reporte](https://mastodon.social/@netblocks/112929340515361487).

Estas acciones limitan las opciones de comunicación segura y plantean la necesidad de explorar alternativas efectivas para evadir la censura.

### Telegram y WeChat: ¿Soluciones Seguras?

Maduro ha promovido las aplicaciones **Telegram** y **WeChat**. Sin embargo, es vital conocer los riesgos que estas aplicaciones representan.

#### Telegram

Aunque [Telegram](https://telegram.org/) es de origen ruso y permite chats encriptados, esta función no está activada por defecto. Además, aunque su código de cliente es de código abierto, el código de los servidores no lo es, lo que genera dudas sobre su seguridad. Por todo ello, se recomienda al público no utilizar esta aplicación para enviar mensajes que puedan estar sometidos al escrutinio de las fuerzas del orden. Sin embargo, Telegram tiene la funcionalidad de comunidades, gracias a la cual distintos medios de comunicación alternativos ofrecen información al público.

#### WeChat

[WeChat](https://www.wechat.com/) es una aplicación permitida en China, país conocido por sus estrictas políticas de control de información. La privacidad en WeChat es limitada, ya que las comunicaciones no están encriptadas y la aplicación recopila numerosos datos de los usuarios. [Leer más](https://siliconangle.com/2023/07/03/wechat-app-anything-private-must-use-heres-protect/).

### Otras Opciones: Signal y Threema

Existen alternativas más seguras como **Signal** y **Threema**. Signal es recomendada por expertos en privacidad, incluido Edward Snowden. Threema se acoje a la legislación Suiza y no recopila datos personales.

#### Signal vs. Threema

No es sencillo determinar cuál es la aplicación más segura, pero hay consideraciones clave:

- **Threema** permite el uso anónimo, sin necesidad de proporcionar datos personales.
- **Signal** también se centra en la seguridad, pero como servicio estadounidense, está sujeto al CLOUD Act, lo que podría implicar la revelación de información personal en los EEUU. 

[Enlace](https://threema.ch/en/messenger-comparison) a la comparación entre Signal y Threema en inglés.

A continuación, una tabla comparativa entre Signal y Telegram:

|                       Función                       |               Signal                |                         Telegram                          |
| :-------------------------------------------------: | :---------------------------------: | :-------------------------------------------------------: |
|                      Gratuito                       |                  X                  |                             X                             |
|              Código de fuente abierta               |                  X                  |                  sólo código de cliente                   |
|            Cifrado de extremo a extremo             |                  X                  |                  sólo en chats secretos                   |
|                 Conforme a la DSGVO                 |                  X                  |                             X                             |
|              Sincronización en la nube              |                  X                  |                             X                             |
|               Plataformas disponibles               | iOS, Android, Versión de escritorio | iOS, Android, Versión de escritorio, Versión de navegador |
| Llamadas de audio / videollamadas / mensajes de voz |                  X                  |                             X                             |
|                       Grupos                        |                  X                  |                             X                             |
|     Lectura automática de contactos telefónicos     |                n.A.                 |                             X                             |
|           Borrado automático de mensajes            |                  X                  |                             X                             |
|        Usabilidad en múltiples dispositivos         |        hasta 5 dispositivos         |                         ilimitado                         |

#### Conclusión: Signal para Venezuela

Considerando la creciente censura, [signal](https://signal.org/) emerge como la opción más viable para la comunicación segura en Venezuela. Su naturaleza gratuita y de código abierto ofrece mayor transparencia y seguridad, aunque [threema](https://threema.ch/) también es una excelente opción para quienes buscan anonimato completo, aunque es una aplicación de pago.

### VPNs: Herramientas para Evasión de la Censura

Para evitar la censura y acceder libremente a internet, las VPNs son herramientas esenciales. [Tor](https://www.torproject.org/) ha sido una de las más importantes, especialmente para periodistas y defensores de derechos humanos. Aquí una tabla comparativa de algunas opciones disponibles:

|  Nombre   | Status |                                                                   iOS (Apple)                                                                   |                                            Android (google)                                             |
| :-------: | :----: | :---------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: |
|    Tor    | gratis | [Enlace Browser](https://apps.apple.com/us/app/onion-browser/id519296448) [Enlace Client VPN](https://apps.apple.com/us/app/orbot/id1609461599) | [Enlace](https://play.google.com/store/apps/details?id=org.torproject.torbrowser&pcampaignid=web_share) |
| Calyx VPN | gratis |                                         [Enlace](https://apps.apple.com/us/app/calyx-vpn/id1539625817)                                          |                    [Enlace](https://f-droid.org/en/packages/org.calyxinstitute.vpn/)                    |
| RiseUpVPN | gratis |                   [Enlace](https://apps.apple.com/us/app/openvpn-connect-openvpn-app/id590379981) + Perfil OpenVPN de RiseUp                    |                                 [Enlace](https://riseup.net/en/android)                                 |
| ProtonVPN |   0$   |                                   [Enlace](https://apps.apple.com/us/app/proton-vpn-fast-secure/id1437005085)                                   |                     [Enlace](https://f-droid.org/en/packages/ch.protonvpn.android)                      |

## Recursos Adicionales

- [Comparación entre Signal, Telegram y WhatsApp](https://clearvpn.com/blog/signal-vs-telegram-vs-whatsapp/)
- [Artículo de Wired sobre Signal](https://www.wired.com/story/signal-politics-software-criticism/)
- [Comentario de Edward Snowden sobre Signal](https://x.com/Snowden/status/1350123606601322496)
- [Comparación Signal vs Threema en Wired](https://www.wired.com/story/signal-politics-software-criticism/)
- [Comparación Signal vs Threema en Brosix](https://www.brosix.com/blog/threema-vs-signal/)
