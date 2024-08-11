---
layout: post
title:  "¿Cómo Evitar el Bloqueo de Internet de CONATEL? Articulo Nr. 2 - HTTPS Block "
date:   2024-08-12 08:00:00 +0100
categories: internet venezuela bloqueo x twitter signal
---

## Resumen rápido (para quien no quiera leer mucho)

Debido los bloqueos de internet en Venezuela, tanto los de DNS como los de tráfico HTTPS, te recomendamos usar una aplicacion VPN. Aquí las recomendadas por nosotros, más abajo hay más opciones. 

| Función / Store |                                                                                                       iOS Apps (Apple)                                                                                                       |                                                                                                  Android Apps (google)                                                                                                  |
| :-------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|       VPN       | [Tor Browser](https://apps.apple.com/us/app/onion-browser/id519296448) - [Tor Cliente VPN](https://apps.apple.com/us/app/orbot/id1609461599), [ProtonVPN](https://apps.apple.com/us/app/proton-vpn-fast-secure/id1437005085) | [Tor](https://play.google.com/store/apps/details?id=org.torproject.torbrowser), [ProtonVPN](https://f-droid.org/en/packages/ch.protonvpn.android/), [CalyxVPN](https://f-droid.org/en/packages/org.calyxinstitute.vpn/) |

Nota: aquí va un [enlace](https://support.signal.org/hc/en-us/articles/360056052052-Proxy-Support) sobre cómo conseguir y utilizar los proxies para Signal y evitar los bloqueos en Venezuela. Enlace en inglés. 

## Bloqueo de tráfico HTTPS por parte de CANTV 

Se dice que CANTV, la principal empresa de telecomunicaciones de Venezuela, ha implementado bloqueos específicos al tráfico HTTPS, afectando a sitios como Binance y ciertos servicios de Microsoft. Este tipo de bloqueo es particularmente preocupante porque el tráfico HTTPS está diseñado para ser seguro y privado, protegiendo la comunicación entre el usuario y el servidor. Sin embargo, supuestamente CANTV ha logrado identificar y restringir el acceso a estos dominios específicos, lo que indica un nivel avanzado de censura y control del tráfico de internet en el país. Los usuarios han reportado dificultades para acceder a estos servicios, lo que sugiere que se están utilizando técnicas de inspección profunda de paquetes (DPI) para detectar y bloquear el tráfico, a pesar de que esté cifrado. Esta acción limita la libertad digital de los venezolanos y genera preocupaciones sobre la privacidad y el acceso a la información en la región.

El bloqueo de tráfico HTTPS es un proceso complejo que puede involucrar varias técnicas avanzadas para restringir el acceso a ciertos sitios web, incluso cuando el tráfico está cifrado. HTTPS (Hypertext Transfer Protocol Secure) es una versión segura del protocolo HTTP, que cifra los datos intercambiados entre el navegador del usuario y el servidor web para proteger la privacidad y seguridad.

### ¿Cómo funciona el bloqueo de tráfico HTTPS?

1. **Inspección Profunda de Paquetes (DPI - Deep Packet Inspection):** 
   - A pesar de que el contenido de las comunicaciones HTTPS está cifrado, algunos metadatos, como el nombre del dominio (SNI - Server Name Indication) y las direcciones IP, no lo están. Los proveedores de servicios de internet (ISP), como CANTV, pueden utilizar técnicas de DPI para analizar estos metadatos y determinar a qué sitios está intentando acceder el usuario.
   - Si el ISP detecta que el tráfico se dirige a un dominio bloqueado, puede interrumpir la conexión o redirigirla a una página de error.

2. **Bloqueo por DNS (Domain Name System):**
   - Los ISP pueden bloquear el acceso a ciertos dominios a nivel de DNS, impidiendo que los usuarios resuelvan el nombre de un dominio en su dirección IP correspondiente. Aunque esto afecta tanto a HTTP como a HTTPS, es una forma común de bloqueo.
   - Sin embargo, los usuarios que configuran sus dispositivos para usar servidores DNS externos o cifrados (como DNS sobre HTTPS o DNS sobre TLS) pueden evadir este tipo de bloqueo, lo que lleva a los ISP a usar técnicas más avanzadas como DPI.

3. **Filtrado de IP:**
   - Algunos ISP pueden bloquear directamente las direcciones IP asociadas a ciertos dominios. Aunque esto puede ser efectivo, puede afectar a otros sitios web que comparten la misma dirección IP o el mismo rango de IP, causando interrupciones en servicios no relacionados.

4. **Inyección de RST (Reset):**
   - Los ISP pueden inyectar paquetes RST en la conexión HTTPS. Un paquete RST indica que la conexión debe ser terminada inmediatamente. Al hacer esto, el ISP fuerza el cierre de la conexión entre el usuario y el servidor, impidiendo el acceso al sitio web bloqueado.

5. **Bloqueo del Certificado TLS/SSL:**
   - En algunos casos, los ISP pueden intentar bloquear o manipular el proceso de intercambio de certificados TLS/SSL. Aunque es más difícil de implementar y puede tener un impacto negativo en la conexión, esta técnica busca impedir que se establezca una conexión segura con ciertos sitios.

### Limitaciones y Evasión

A pesar de estas técnicas, existen métodos que los usuarios pueden utilizar para evadir el bloqueo, como el uso de redes privadas virtuales (VPN), servicios de proxy, y DNS cifrados. Estos métodos hacen más difícil para el ISP identificar y bloquear el tráfico, ya que ocultan los metadatos que normalmente se utilizan para la inspección.


### Tabla de VPNs 

También puede interesarle otros servicios de VPN disponibles en la siguiente tabla. Por ejemplo, Tunnel Bear hizo recientemente un anuncio dirigido a los usuarios venezolanos. Aqui el [enlace](https://x.com/theTunnelBear/status/1821939428924780924)


|   Nombre    |         Status/Enlace         |                                                                    iOS (Apple)                                                                    |                                            Android (google)                                             |
| :---------: | :---------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: |
|     Tor     |            gratis             | [Enlace Browser](https://apps.apple.com/us/app/onion-browser/id519296448) - [Enlace Client VPN](https://apps.apple.com/us/app/orbot/id1609461599) | [Enlace](https://play.google.com/store/apps/details?id=org.torproject.torbrowser&pcampaignid=web_share) |
|  Calyx VPN  |            gratis             |                                          [Enlace](https://apps.apple.com/us/app/calyx-vpn/id1539625817)                                           |                    [Enlace](https://f-droid.org/en/packages/org.calyxinstitute.vpn/)                    |
|  RiseUpVPN  |     <https://riseup.net/>     |                    [Enlace](https://apps.apple.com/us/app/openvpn-connect-openvpn-app/id590379981) + Perfil OpenVPN de RiseUp                     |                                 [Enlace](https://riseup.net/en/android)                                 |
|  ProtonVPN  |    0$ <https://proton.me/>    |                                    [Enlace](https://apps.apple.com/us/app/proton-vpn-fast-secure/id1437005085)                                    |                     [Enlace](https://f-droid.org/en/packages/ch.protonvpn.android)                      |
| Tunnel Bear | <https://www.tunnelbear.com/> |                                  [Enlace](https://apps.apple.com/us/app/tunnelbear-secure-vpn-wifi/id564842283)                                   |             [Enlace](https://play.google.com/store/apps/details?id=com.tunnelbear.android)              |
|  Touch VPN  |  <https://www.touchvpn.net/>  |                                      [Enlace](https://apps.apple.com/us/app/touch-vpn-secure-hotspot-proxy/)                                      |             [Enlace](https://play.google.com/store/apps/details?id=com.northghost.touchvpn)             |
|   Psiphon   |     <https://psiphon.ca/>     |                                           [Enlace](https://apps.apple.com/us/app/psiphon/id1276263909)                                            |                  [Enlace](https://play.google.com/store/apps/details?id=com.psiphon3)                   |
|   Lantern   |     <https://lantern.io/>     |                                         [Enlace](https://apps.apple.com/ae/app/lantern-vpn/id1457872372)                                          |             [Enlace](https://play.google.com/store/apps/details?id=org.getlantern.lantern)              |

## Enlances
- [https://www.lapatilla.com/2024/08/10/denuncian-el-bloqueo-de-la-web-de-mercado-libre-en-venezuela/](https://www.lapatilla.com/2024/08/10/denuncian-el-bloqueo-de-la-web-de-mercado-libre-en-venezuela/)
- [Reportan Bloqueo de la página de mercado libre y binance en el pais](https://elperiodiquito.com/venezuela/178789/reportan-bloqueo-de-la-pagina-de-mercado-libre-y-binance-en-el-pais/)
- [VE sin Filtro: Más de 550 eventos de bloqueos en Internet evidencian la censura y las limitaciones a los derechos humanos en Venezuela](https://vesinfiltro.com/noticias/2024-03-12-Censura-internet/)
- [VE sin Filtro denuncia bloqueo de Binance y Mercado Libre en Venezuela #10Ago](https://www.elimpulso.com/2024/08/10/ve-sin-filtro-denuncia-bloqueo-de-binance-y-mercado-libre-en-venezuela-10ago/)
- [Golpe cripto: Cantv también aplicó bloqueo a Binance](https://www.elimpulso.com/2024/08/10/ve-sin-filtro-denuncia-bloqueo-de-binance-y-mercado-libre-en-venezuela-10ago/)
- [Cantv también bloqueó dominios de Microsoft en Venezuela](https://porlavision.com/cantv-tambien-bloqueo-dominios-de-microsoft-en-venezuela/)