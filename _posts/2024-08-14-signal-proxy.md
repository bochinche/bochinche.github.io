---
layout: post
title:  "¿Cómo ayudar a otros a conectarse a Signal mediante un proxy? Una guía práctica"
date:   2024-08-14 08:00:00 +0100
categories: venezuela signal proxy block SignalProxy
--- 

**\#SignalProxy**

# Proxy, por favor: Ayuda a la gente a conectarse a Signal 
*(traducción del artículo original)* 

**Meredith Whittaker, 9 de agosto de 2024**

En los últimos tiempos, varios países han bloqueado el acceso a Signal, dejando a sus residentes sin un espacio seguro y confiable para comunicarse. En respuesta, Signal ha implementado herramientas para eludir la censura, incluyendo soporte para un proxy TLS simple, que en muchas situaciones puede evitar estos bloqueos y permitir que las personas se conecten de manera privada.

Para activar la función integrada de elusión de censura en Signal, dirígete a **Configuración de Signal > Privacidad > Avanzado > Elusión de la censura**.

El proxy TLS de Signal es compatible tanto con Signal para Android como para iOS. Esta herramienta puede ser usada para evitar bloqueos de red, redirigiendo el tráfico de manera segura hacia los servidores de Signal. Cualquiera puede configurar un proxy, y una vez implementado, podrás compartir una URL que permitirá a otros conectarse fácilmente. Solo es necesario tocar la URL en un dispositivo móvil para que Signal comience a usar el proxy automáticamente.

Si deseas más información sobre cómo conectarte a un servidor proxy de Signal o cómo gestionar la configuración de tu proxy, visita nuestro [Centro de Soporte](https://support.signal.org/hc/en-us/articles/360056052052-Proxy-Support).

## Tu ayuda es crucial

Para maximizar la efectividad de nuestras herramientas de elusión, invitamos a quienes puedan y deseen configurar sus propios servidores proxy a que lo hagan, siguiendo las instrucciones disponibles [aquí](https://github.com/signalapp/Signal-TLS-Proxy).

Esta no es la primera vez que enfrentamos estos desafíos. Anteriormente, en [2021](https://signal.org/blog/help-iran-reconnect/) y [2022](https://signal.org/blog/run-a-proxy/), compartimos guías sobre el uso de proxies, y en ambas ocasiones la comunidad respondió de manera sobresaliente, expandiendo nuestra cobertura de manera significativa. Agradecemos profundamente su generosidad y compromiso, tanto entonces como ahora. Nuestra esperanza es que estos esfuerzos ayuden a las personas a acceder a Signal, incluso bajo bloqueos gubernamentales, mientras continuamos explorando nuevas técnicas para asegurar que Signal esté disponible para todos aquellos que lo necesiten.

## Sé el proxy

Si deseas operar un servidor proxy, puedes seguir las instrucciones de configuración actualizadas [aquí](https://github.com/signalapp/Signal-TLS-Proxy).

Las aplicaciones de Signal para Android y iOS están configuradas para manejar enlaces desde el dominio `signal.tube`, permitiendo la configuración automática del proxy al tocar un enlace desde cualquier otra aplicación. También es posible configurar manualmente la información del proxy en los ajustes de Signal:

- **Android:** Configuración de Signal > Datos y almacenamiento > Proxy > Usar proxy
- **iOS:** Configuración de Signal > Privacidad > Avanzado > Proxy > Usar proxy

A diferencia de un proxy HTTP estándar, las conexiones al proxy TLS de Signal se presentan como tráfico web cifrado normal. No se utilizan métodos que puedan delatar a los censores que se está empleando un proxy. Además, se proporcionan certificados TLS válidos para cada servidor proxy, lo que dificulta a los censores identificar el tráfico, algo que sería más fácil si se usaran certificados autofirmados. En resumen, todo está diseñado para ser lo más discreto posible.

El cliente de Signal establece una conexión TLS normal con el proxy, que simplemente reenvía los datos al servidor real de Signal. Cualquier tráfico que no provenga de Signal es bloqueado, y el cliente de Signal sigue negociando su conexión TLS directamente con los puntos finales de Signal a través de este túnel. Esto asegura que, además del cifrado de extremo a extremo que ya protege todas las comunicaciones en Signal, todo el tráfico permanece opaco incluso para el operador del proxy.

## Corre la voz: Utiliza el hashtag \#SignalProxy

Si configuras un proxy para Signal, es importante darlo a conocer para que otros puedan utilizarlo. Utiliza el hashtag **#SignalProxy** en las plataformas sociales para facilitar su descubrimiento.

Sin embargo, al compartir públicamente un enlace a `signal.tube` o si un servidor se vuelve muy popular, aumenta la probabilidad de que los censores bloqueen esas direcciones IP. Una alternativa más discreta sería anunciar que has creado un proxy para Signal y ofrecerte a compartir los detalles de conexión a través de mensajes directos o no públicos. Por ejemplo:

> "Responde a este hilo si quieres los detalles de conexión de mi #SignalProxy, o envíame un DM para que pueda compartir el enlace contigo."

Es fácil lanzar nuevos proxies, y mientras haya servidores disponibles, no hay límite en la cantidad de proxies TLS de Signal que se pueden implementar.

## Terreno inestable

El mundo cambia de manera impredecible, y nosotros continuaremos esforzándonos para mantener Signal accesible para todos aquellos que lo necesiten, en cualquier momento. Gracias por tu apoyo.

*Este artículo es una traducción del original.*


## Enlaces 
- [Proxy Please: Help People Connect to Signal](https://signal.org/blog/proxy-please/)
- [Código Fuente Signal TLS Proxy](https://github.com/signalapp/Signal-TLS-Proxy)
