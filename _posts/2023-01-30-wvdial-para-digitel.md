---
layout: post
title:  "Configuración de wvdial para Digitel (Venezuela)"
date:   2023-01-30 08:00:00 +0100
categories: IT Venezuela digitel
---

## Introducción
En muchas ocasiones, cuando intentamos utilizar un módem USB 3G en Linux, nos encontramos con la necesidad de configurarlo manualmente para que funcione correctamente. Uno de los métodos más comunes y efectivos es a través de `wvdial`, una herramienta que permite la conexión a internet mediante módems analógicos y 3G. En este artículo, te guiaré paso a paso para configurar y utilizar `wvdial` con un dongle 3G Huawei.


### Paso 1: Instalación de wvdial
Antes de empezar con la configuración, asegúrate de que tienes `wvdial` instalado en tu sistema. Puedes instalarlo usando el gestor de paquetes de tu distribución de Linux. En Debian, Ubuntu y derivados, puedes utilizar:

```bash
sudo apt-get install wvdial
```

### Paso 2: Configuración de wvdial
Una vez que tienes `wvdial` instalado, el siguiente paso es configurar el archivo de configuración `/etc/wvdial.conf`. Este archivo contiene todos los parámetros necesarios para que el dongle se conecte correctamente.

#### Archivo de configuración: /etc/wvdial.conf
```bash
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","gprsweb.digitel.ve"
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = Digitel
Password = Digitel
Modem = /dev/ttyUSB0
Baud = 460800
```

Descripción de los parámetros:
- Init1, Init2, Init3: Estos comandos inicializan el módem. En particular, `AT+CGDCONT` establece el contexto PDP, donde "gprsweb.digitel.ve" es el APN (Access Point Name) de la red móvil.
- Modem: Define el dispositivo que corresponde al módem. En este caso, es `/dev/ttyUSB0`.
- Phone: El número que se marca para la conexión, en este caso, `*99#`.
- Username y Password: Las credenciales necesarias para autenticarse en la red.
- Baud: La velocidad de la conexión entre el módem y la computadora.



### Paso 3: Configuración adicional en ppp
Para asegurar que `wvdial` maneje la conexión de manera eficiente, necesitas ajustar algunos parámetros en el archivo `/etc/ppp/peers/wvdial`. Este archivo ayuda a manejar los detalles de la conexión PPP (Point-to-Point Protocol).

#### Archivo de configuración: /etc/ppp/peers/wvdial
```bash
noauth
name wvdial
usepeerdns
defaultroute
replacedefaultroute
```

Descripción de los parámetros:
- noauth: Desactiva la autenticación de PPP, ya que `wvdial` se encarga de ella.
- name wvdial: Define el nombre de usuario que se utilizará para la conexión.
- usepeerdns: Utiliza los servidores DNS proporcionados por la red.
- defaultroute y replacedefaultroute: Estas opciones garantizan que la ruta predeterminada del sistema utilice la conexión establecida por `wvdial`.


### Paso 4: Conectando a Internet
Una vez que la configuración esté completa, simplemente puedes iniciar la conexión con el siguiente comando:

```bash
sudo wvdial
```

`wvdial` tomará los parámetros de configuración y tratará de establecer una conexión a internet. Si todo está configurado correctamente, verás una serie de mensajes indicando que la conexión se ha establecido con éxito.

### Conclusión
Con estos sencillos pasos, deberías poder conectar tu 3G Dongle Huawei a internet en un sistema Linux utilizando `wvdial`. Esta herramienta es particularmente útil en entornos donde las opciones gráficas son limitadas o en sistemas ligeros. Recuerda que los APN y credenciales pueden variar dependiendo de tu proveedor de servicios, así que asegúrate de ajustarlos según tus necesidades.


