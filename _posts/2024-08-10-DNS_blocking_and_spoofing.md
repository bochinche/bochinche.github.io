---
layout: post
title:  "¿Cómo Evitar el Bloqueo de Internet de CONATEL? Articulo Nr. 1 - Suplantación y bloqueo de DNS"
date:   2024-08-10 08:00:00 +0100
categories: IT venezuela bloqueo dns
---

## Resumen rápido (para quien no quiera leer mucho)

- Para computadores portátiles, de escritorio, así como para móviles, recomendamos usar la aplicación WARP, de Cloudflare, que puedes encontrar en este [enlace](https://one.one.one.one/). 
- Para modems y enrutadores (routers), recomendamos utilizar estos servidores DNS en vez de los que proporciona tu proveedor de internet.

| Proveedor de DNS | Servidor DNS 1 | Servidor DNS 1 |
| :--------------: | :------------: | :------------: |
|    Cloudflare    |    1.1.1.1     |    1.1.2.2     |
|     OpenDNS      | 208.67.222.222 | 208.67.220.220 |
|      Google      |    8.8.8.8     |    8.8.4.4     |

Nota: nuestra recomendación es utilizar los servidores DNS de OpenDNS o Cloudflare, ya que Google guarda la información para crear perfiles de marketing y publicidad. 

### Cómo Evitar el Bloqueo de Internet de CONATEL: Métodos y Soluciones

En un artículo [anterior](https://bochinche.github.io/internet/venezuela/bloqueo/x/twitter/signal/2024/08/08/overcoming-blockade-vzla.html), exploré diversas soluciones prácticas para esquivar los bloqueos de Internet que está implementando [CONATEL](http://www.conatel.gob.ve/). Ahora, profundizaremos en uno de los métodos más comunes que se están utilizando para limitar el acceso a la red y, lo más importante, cómo podemos superarlo.

#### Bloqueo de DNS: ¿Cómo Funciona?

En Internet, cada dominio o subdominio que usamos, como **google.com**, debe traducirse a una dirección IP, como **8.8.8.8**, para que los navegadores puedan acceder a la página web deseada. Esta conversión es realizada por el Sistema de Nombres de Dominio, conocido como **DNS** por sus siglas en inglés *Domain* *Name* *Service*. Todos nuestros dispositivos, desde teléfonos móviles hasta módems y routers domésticos, dependen de este sistema para navegar por la web. En la mayoría de los casos, el servidor DNS que utilizamos es configurado automáticamente por nuestro proveedor de servicios de Internet (ISP).

Dado este proceso, una de las maneras más simples y efectivas para bloquear el acceso a ciertos servicios de Internet, como **x.com** o **twitter.com**, es ordenando a los ISPs, como Digitel, Movistar o NetUno, que modifiquen sus servidores DNS para no responder correctamente a las solicitudes de estos dominios (DNS Blocking). En el peor de los casos, podrían redirigirnos a una dirección IP incorrecta, impidiendo así que accedamos al contenido deseado (DNS Spoofing).

#### ¿Cómo Superar el Bloqueo de DNS?

Afortunadamente, existen varias estrategias que podemos adoptar para evadir estos bloqueos y restaurar nuestro acceso a la web:

**1. Cambiar el DNS en tu Módem/Router:**

Si tienes acceso a la configuración de tu módem o router en casa, puedes cambiar manualmente el servidor DNS que utilizas. Algunas opciones populares y confiables incluyen los DNS de Google (8.8.8.8 y 8.8.4.4), Cloudflare (1.1.1.1) u OpenDNS (208.67.222.222 y 208.67.220.220). Este cambio es relativamente sencillo y puede hacerse directamente desde la interfaz de configuración del dispositivo. Nuestra recomendación es utilizar los servidores DNS de OpenDNS o Cloudflare, ya que Google guarda la información para crear perfiles de marketing y publicidad. 

**2. Soluciones para Dispositivos Móviles y Computadoras:**

Además de modificar la configuración del DNS en tu dispositivo, puedes utilizar aplicaciones especializadas para mejorar la seguridad y la privacidad de tu conexión. Una excelente opción es WARP, una aplicación desarrollada por Cloudflare. WARP crea una especie de "semi-VPN" que asegura que todo el tráfico DNS pase por un túnel seguro, lo que ayuda a eludir cualquier bloqueo impuesto por tu ISP. Esta aplicación está disponible tanto para dispositivos móviles como para computadoras, y es fácil de instalar y usar. Es importante destacar que, en su configuración más básica, WARP no es una VPN completa.

#### Ventajas de Estas Soluciones

La mayor ventaja de estas solución, WARP, es que solo el tráfico DNS será redirigido a través del túnel VPN, lo que significa que tu conexión general a Internet permanecerá rápida y sin interrupciones. Además, estas solución son fáciles de implementar, incluso para usuarios con conocimientos técnicos limitados, y ofrecen una capa adicional de seguridad y privacidad al navegar.

En conclusión, aunque los bloqueos de DNS pueden parecer una barrera formidable, existen métodos eficaces y accesibles para superarlos. Cambiar el servidor DNS o utilizar aplicaciones como WARP son soluciones prácticas que pueden ayudarte a mantener tu acceso a Internet sin restricciones.

Pronto publicaremos otro artículo en el que profundizaremos en el tema y otras soluciones que nos podrán ayudar.

### Enlaces 
- [VE sin Filtro: Más de 550 eventos de bloqueos en Internet evidencian la censura y las limitaciones a los derechos humanos en Venezuela](https://vesinfiltro.com/noticias/2024-03-12-Censura-internet/)