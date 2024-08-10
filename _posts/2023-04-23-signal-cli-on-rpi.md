---
layout: post
title:  "¿Cómo utilizar Signal-Cli en un Raspberry Pi para enviar mensajes seguros?"
date:   2023-04-23 08:00:00 +0100
categories: IT rpi
---

En un mundo donde la privacidad digital es cada vez más valorada, herramientas como Signal han ganado popularidad por ofrecer comunicación segura y cifrada. En este artículo, te enseñaremos cómo configurar y utilizar Signal-Cli en un Raspberry Pi para enviar mensajes de manera segura. Signal-Cli es una herramienta de línea de comandos que permite interactuar con la plataforma de mensajería Signal sin necesidad de una interfaz gráfica, lo que lo convierte en una opción ideal para proyectos en dispositivos como el Raspberry Pi.

## Requisitos Previos

Antes de comenzar con la instalación y configuración de Signal-Cli, necesitas asegurarte de que tu Raspberry Pi cumpla con los siguientes requisitos:

1. **Raspberry Pi**: Un modelo con Raspbian (ahora Raspberry Pi OS) instalado.
2. **Java Runtime Environment (JRE)**: Signal-Cli está escrito en Java, por lo que necesitarás tener JRE instalado.
3. **Acceso a Internet**: Para descargar los archivos necesarios y registrar tu número de teléfono en Signal.

## Paso 1: Instalar Java en tu Raspberry Pi

Primero, necesitamos instalar Java, ya que Signal-Cli depende de este para funcionar. Puedes hacerlo fácilmente con el siguiente comando:

```bash
sudo apt update
sudo apt install default-jre
```

Esto instalará la última versión del entorno de ejecución de Java disponible en los repositorios oficiales de Raspbian.

## Paso 2: Descargar Signal-Cli y Librerías de Signal

Ahora que Java está instalado, el siguiente paso es descargar Signal-Cli y las librerías necesarias. Dirígete a los siguientes enlaces para obtener los archivos más recientes:

- Descarga Signal-Cli desde [aquí](https://github.com/AsamK/signal-cli/releases).
- Descarga las librerías de Signal necesarias desde [este repositorio](https://github.com/exquo/signal-libs-build).

Alternativamente, puedes descargar estas herramientas directamente en tu Raspberry Pi usando `wget`:

```bash
wget https://github.com/AsamK/signal-cli/releases/download/v0.10.10/signal-cli-0.10.10-Linux.tar.gz
wget https://github.com/exquo/signal-libs-build/releases/download/v0.22.2/libsignal-client-linux-aarch64-0.22.2.so
```

Después de descargar los archivos, descomprime Signal-Cli:

```bash
tar -xvzf signal-cli-0.10.10-Linux.tar.gz
```

Copia la librería descargada al directorio de Signal-Cli:

```bash
cp libsignal-client-linux-aarch64-0.22.2.so signal-cli/lib/
```

## Paso 3: Registrar tu Número de Teléfono

Antes de poder enviar mensajes, debes registrar tu número de teléfono en la red de Signal. Para hacerlo, ejecuta el siguiente comando:

```bash
./signal-cli/bin/signal-cli -u +1234567890 register
```

Asegúrate de reemplazar `+1234567890` con tu número de teléfono. Este comando enviará un código de verificación a tu teléfono. Una vez recibido, verifica tu número de la siguiente manera:

```bash
./signal-cli/bin/signal-cli -u +1234567890 verify 123456
```

## Paso 4: Enviar Mensajes

Con Signal-Cli configurado y tu número verificado, ya puedes empezar a enviar mensajes. La sintaxis básica para enviar un mensaje es la siguiente:

```bash
./signal-cli/bin/signal-cli -u +1234567890 send -m "Tu mensaje aquí" +0987654321
```

En este comando, `+1234567890` es tu número registrado y `+0987654321` es el número del destinatario. El parámetro `-m` indica el mensaje que deseas enviar.

## Paso 5: Automatización y Scripting

Una de las mayores ventajas de utilizar Signal-Cli en un Raspberry Pi es la posibilidad de automatizar el envío de mensajes. Puedes escribir scripts en bash o cualquier otro lenguaje compatible para enviar mensajes automáticamente en base a eventos específicos, como alertas de seguridad, notificaciones de sistema, o cualquier otra necesidad.

### Ejemplo de Script

Aquí tienes un ejemplo simple de un script en bash que envía un mensaje cuando la CPU del Raspberry Pi supera un cierto umbral de temperatura:

```bash
#!/bin/bash
TEMP=$(vcgencmd measure_temp | egrep -o '[0-9]*\.[0-9]*')
THRESHOLD=70.0

if (( $(echo "$TEMP > $THRESHOLD" |bc -l) )); then
    ./signal-cli/bin/signal-cli -u +1234567890 send -m "Alerta: Temperatura de CPU alta: $TEMP°C" +0987654321
fi
```

Este script puede ser configurado para ejecutarse periódicamente usando `cron`, el programador de tareas en Linux.

## Conclusión

El uso de Signal-Cli en un Raspberry Pi es una excelente manera de aprovechar la potencia de la mensajería segura de Signal en proyectos que requieren automatización o control remoto sin necesidad de una interfaz gráfica. Ya sea para enviar alertas, notificaciones, o simplemente mantenerte en contacto de forma segura, Signal-Cli te ofrece una solución flexible y robusta.

Si sigues estos pasos, deberías estar listo para empezar a enviar mensajes seguros desde tu Raspberry Pi. ¡Buena suerte!
# Enlaces

- [libsignal_v0.22.2](https://github.com/exquo/signal-libs-build/releases)
- [signal-cli](https://github.com/AsamK/signal-cli/releases)
- [https://github.com/exquo/signal-libs-build](https://github.com/exquo/signal-libs-build)
- [https://medium.com/@dogukanakkaya/how-to-send-signal-messages-with-signal-cli-21f6fa1c7d58](https://medium.com/@dogukanakkaya/how-to-send-signal-messages-with-signal-cli-21f6fa1c7d58)