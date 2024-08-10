---
layout: post
title:  "¿Cómo instalar una impresora PDF en CUPS para Apple Print?"
date:   2023-04-22 08:00:00 +0100
categories: IT rpi
---

En este artículo, te guiaré paso a paso sobre cómo instalar y configurar una impresora PDF en CUPS, que sea compatible con Apple Print mediante el uso de AirPrint. Este proceso te permitirá imprimir documentos en formato PDF desde dispositivos Apple, como iPhones y iPads, directamente a un servidor Linux con CUPS. Para esta guía, utilizaremos recursos y herramientas disponibles en varios sitios confiables.

### Requisitos Previos

Antes de comenzar, asegúrate de tener lo siguiente:

1. **Un servidor Linux con CUPS instalado** (puede ser una distribución basada en Debian, como Ubuntu).
2. **Acceso a la línea de comandos** con privilegios de superusuario.
3. **Paquetes necesarios instalados**: `cups`, `cups-pdf`, y `avahi-daemon`.

### Paso 1: Instalar CUPS y Configurar la Impresora PDF

Primero, necesitas instalar CUPS y el controlador de impresora PDF. Esto se puede hacer con los siguientes comandos:

```bash
sudo apt update
sudo apt install cups cups-pdf avahi-daemon
```

#### Configurar CUPS

Una vez instalados, debes configurar CUPS para que pueda ser administrado a través de su interfaz web. Edita el archivo de configuración:

```bash
sudo nano /etc/cups/cupsd.conf
```

En este archivo, asegúrate de cambiar las líneas correspondientes para permitir el acceso desde cualquier dirección IP:

```plaintext
Listen 631
Port 631
```

Debajo de `<Location /admin>` y `<Location /admin/conf>` cambia `Require user @SYSTEM` a `Require valid-user`, y permite el acceso desde cualquier dirección:

```plaintext
Order allow,deny
Allow all
```

Guarda y cierra el archivo. Luego, reinicia el servicio de CUPS:

```bash
sudo systemctl restart cups
```

#### Agregar la Impresora PDF

Puedes agregar la impresora PDF desde la interfaz web de CUPS:

1. Abre un navegador y dirígete a `http://localhost:631`.
2. Ve a la sección "Administración" y selecciona "Agregar impresora".
3. Elige `PDF (Virtual PDF Printer)` y sigue los pasos para configurarla.
4. Configura la impresora para que guarde los archivos PDF en un directorio específico, como `/var/spool/cups-pdf/ANONYMOUS`.

### Paso 2: Configurar AirPrint para Apple Print

Para que la impresora PDF sea detectada por dispositivos Apple a través de AirPrint, necesitamos configurar Avahi y crear un archivo de servicio AirPrint.

#### Configurar Avahi

Edita el archivo de configuración de Avahi:

```bash
sudo nano /etc/avahi/avahi-daemon.conf
```

En este archivo, asegúrate de que las siguientes opciones estén habilitadas:

```plaintext
use-ipv4=yes
use-ipv6=yes
```

Guarda y cierra el archivo, y luego reinicia Avahi:

```bash
sudo systemctl restart avahi-daemon
```

#### Crear un Archivo de Servicio AirPrint

Usaremos el script `airprint-generate` para generar un archivo de servicio compatible con AirPrint:

1. Clona el repositorio `airprint-generate` desde GitHub:

```bash
git clone https://github.com/tjfontaine/airprint-generate.git
cd airprint-generate
```

2. Ejecuta el script para crear el archivo de servicio:

```bash
./airprint-generate.py -d /etc/avahi/services
```

Esto creará un archivo `.service` en el directorio `/etc/avahi/services` que Avahi utilizará para anunciar la impresora PDF como una impresora AirPrint.

### Paso 3: Probar la Configuración

Finalmente, para probar la configuración, asegúrate de que tu dispositivo Apple esté en la misma red que el servidor Linux. Abre cualquier documento en tu iPhone o iPad, selecciona "Imprimir" y deberías ver la impresora PDF disponible en la lista.

Si todo está configurado correctamente, al imprimir, se generará un archivo PDF en el directorio que configuraste en CUPS.

### Conclusión

Siguiendo estos pasos, habrás configurado una impresora PDF en un servidor CUPS compatible con Apple Print a través de AirPrint. Esto te permitirá imprimir documentos desde cualquier dispositivo Apple directamente a un PDF almacenado en tu servidor Linux.

Para más detalles, puedes consultar la [documentación oficial de CUPS-PDF](https://www.cups-pdf.de/documentation.shtml) y otras fuentes útiles como [LinuxBabe](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint) o el [wiki de Debian sobre impresión sin drivers](https://wiki.debian.org/CUPSDriverlessPrinting).

¡Buena suerte con tu instalación!

### Enlaces
- <https://github.com/tjfontaine/airprint-generate>
- <https://wiki.debian.org/CUPSDriverlessPrinting>
- <https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint>
- <https://www.cups-pdf.de/documentation.shtml>
- <https://www.elektronik-kompendium.de/sites/raspberry-pi/2007081.htm>