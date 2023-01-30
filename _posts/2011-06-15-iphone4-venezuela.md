---
layout: post
title:  "sobre el iPhone 4 en Venezuela: Digitel y Movistar"
date:   2011-06-15 17:45:47 +0100
categories: IT
---
# Version en Castellano
Anglicismos utilizados en este artículo:

- simlock –> bloqueo de la tarjeta SIM
- unlock –> desbloqueo
- carrier –> operador móvil
- hot-spot –> punto de acceso
- jailbreak –> fuga de la cadena de confianza

El iPhone 4 salió al mercado internacional hace más o menos un año. En Venezuela el primer operador móvil que lo sacó al mercado en su versión GSM fue movistar. No hace mucho, Digitel, otro operador móvil Venezolano sacó alternativamente el iPhone 4 al mercado Venezolano. En estos momentos hay versiones contradictorias acerca del servicio de “hotspot” adicional que permite conectar  a internet otros equipos informáticos adicionales a través de bluetooth, cable de datos o red WIFI inalámbrica (ver links 1 y 2).

Lo primero que llama la atención es que mientras en que en países como: Bélgica, Canadá, Alemania, Ecuador, México, Alemania, Rusia, España, Reino Unido, entre otros, equipos iPhone 4 e iPhone 3GS pueden ser adquiridos sin el llamado “simlock” (ver link 3), en Venezuela ninguno de los dos carriers que  promueven los iPhones ofrecen esta opción. En algunos de los países mencionados anteriormente, los operadores también están obligados a desbloquear los equipos una vez culminado el contrato de servicio.

## ¿Qué es simlock? 
El simlock es una técnica que implementan los fabricantes de equipos móviles para que éstos sólo puedan utilizar tarjetas SIM de un operador móvil específico. Esta técnica es usada para permitir que los operadores móviles puedan subvencionar los equipos a sus usuarios durante la duración de un contrato de telefonía móvil. De esta manera los usuarios no podrán utilizar el equipo con operadores móviles alternativos.

## ¿Que es la función de “hotspot”? 
El iPhone, al igual que muchos otros equipos, permite compartir su conexión de datos a internet mediante una técnica llamada tethering. Al principio esta técnica no fue aceptada por los operadores móviles principalmente AT&T en los EEUU, ya que permitía a los usuarios conectarse a internet desde un ordenador portátil a través del iPhone. De esta manera muchos usuarios lograron sobrecargar la red de datos de AT&T de modo tal que no funcionaba de manera confiable. AT&T a venido cambiando esos contratos que otorgaban planes de datos ilimitados a sus usuarios por contratos con planes en los cuales la velocidad de conexión es reducida si el usuario excede cierta cantidad de datos por mes.

La función de “hotspot” fue introducida oficialmente por Apple con el iOS v4, aunque ya había sido implementada usando programas que eran instalados usando una técnica denominada jailbreak.

## ¿Qué es el iOS?
El iOS es el sistema operativo de los iDevices: iPhone, iPad, iPod Touch. En estos momentos la versión actual es la 4.3.3 y Apple está probando la nueva generación denominada iOS 5.

## ¿Qué es el jailbreak? 
El jailbreak es una técnica que inhibe el “trust-chain” (cadena de confianza) de modo que programas que no son permitidos explícitamente por Apple puedan correr en el iPhone. De esta manera se pueden instalar programas que permiten la función de hotspot, programas para desactivar el simlock, entre otros. Este método no es deseado por Apple, todo lo contrario, en el caso de que un usuario lo implemente pierde la garantía de su equipo. Sin embargo en el caso de que su equipo presente algún defecto, usted puede volver a instalar el iOS original de Apple en su equipo, y la empresa no le dará problemas a la hora de efectuar un trabajo bajo garantía. En cuanto a la legalidad de este método, la corte suprema de los EEUU determinó que en los EEUU era completamente legal (link 7).

Una vez aclarados estos aspectos técnicos la pregunta de las mil lochas es ¿cómo hacer para inhibir el simlock de mi iPhone para poder usar cualquier SIM (o micro-SIM) independientemente del operador móvil?

En primer lugar debemos aclarar ¿por qué queremos un iPhone desbloqueado?
Seguramente muchas personas tendrán respuestas distintas a estas preguntas, sin embargo, creo que las más importantes son:

- la libertad de elegir entre cualquier proveedor de servicios de telefonía móvil
- la posibilidad de re-vender el equipo a otra persona que use otro proveedor de telefonía móvil
- la posibilidad de ahorrar costos en el extranjero usando tarjetas SIM prepagadas EEUU, Europa y Asia.
siendo la última opción la que más le afecta a los proveedores de servicios de telefonía móvil ya que ellos cargan montos exorbitantes por el llamado roaming internacional.

## ¿Cómo se puede desbloquear in iPhone?
La primera opción que tenemos es a través de el llamado NCK, un código que nos proporciona Apple y es único para cada dispositivo. Sin embargo este código sólo lo proporciona Apple, si el operador móvil conviene a hacerlo. Este no es el caso en Venezuela, por lo que ahí no tenemos ninguna posibilidad.
La segunda opción es través del software. Para poder hacer un desbloqueo, primero hay que hacer un jailbreak. Una vez hecho el jailbreak el usuario debe instalar un programa llamado ultrasn0w que logra inyectar un vector de crakeo al iPhone y de esta manera inhibir el simlock (el link 8 contiene instrucciones para éste método).
La tercera posibilidad es haciendo uso de los llamados turbo-sims o de los gevey sims. Esta opción incluye la compra de un adaptador de sim adicional y en muchos casos requiere de bastante paciencia.
Obviamente la mejor manera de hacer el unlock es a través de la primera. Sin embargo, lastimosamente vivimos en un país en el cual la voluntad política no va acorde con los intereses del pueblo sino a favor de los grandes capitales. En contraste con otros países, Venezuela no cuenta una legislación que obligue a los operadores móviles a deshabilitar el simlock una vez finalizado el contrato. (Nota: ojalá este comentario llegue a nuestros legisladores y éstos efectúen un cambio en la legislación)

La segunda opción representa una alternativa gratis para desbloquear el iPhone gracias a un equipo de hackers denominado “dev-team” (link 5) quienes hacen ese trabajo de manera gratuita, y publican el código fuente de su trabajo bajo una licencia gratis: GPL.  El “dev-team“  ofrece varios programas que en primer lugar le hacen un jailbreak a su iPhone: redsn0w y Pwnage Tool, y otro denominado untrasn0w que permite hacerle el desbloqueo al teléfono. Aunque el  ”dev-team” ha hecho un trabajo excepcional, hasta los momentos el desbloqueo sólo funciona con ciertas versiones de iOS y el baseband. Hasta la fecha, la última versión del baseband no ha sido desbloqueada.
Es importante resaltar que el código fuente de estos programas ha sido publicado! Esto asegura que muchos programadores tengan acceso al código fuente y, en caso tal, pudieran corregir errores o darse cuenta si hay virus o código maligno.

La tercera opción, es una opción basada en un adaptador de sim y trabaja a ese nivel. Por ser la opción más cara, y por el hecho de que Apple continuamente cambia su técnica para deshabilitar estas tarjetas, esta debería ser la última técnica en ser usada. El proveedor de estos adaptadores el la empresa applenberry (link 6).

## ¿Que es el baseband?
El baseband es el software que controla al chip GSM del iPhone. Hasta los momentos todos los un-locks ofrecidos por el “dev-team” aprovechaban errores de programación del baseband para poder inyectar vectores de hackeo y desabilitar el sim-lock. El último baseband del iPhone 4 no ha podido ser hackeado. El “dev-team” está trabajando en alguna forma de hackear este baseband.

## Recomendaciones
He visto mucha gente en mercadolibre.com.ve o en youtube ofreciendo sus servicios, con precios exagerados, para efectuar el desbloqueo de su iPhone. En el caso de que usted no tenga un iOS muy actualizado es muy posible que usted puede realizar el desbloqueo de su iPhone usted mismo sin costo adicional alguno.
Conocimientos técnicos no son realmente necesarios! En la siguiente página se le ofrece más información de como realizar el desbloqueo y si su iPhone aplica para esta solución por software: iClarified.

En el caso de que su versión del iOS sea la más actual y usted no pueda hacer un unlock vía software, la alternativa es el adaptador sim de gevey. En estos momentos éstos se consiguen por 150 BsF. en mercadolibre.com.ve

---

# English Version
The iPhone 4 was released internationally about a year ago. In Venezuela the first mobile operator to release it in its GSM version was Movistar. Not long ago, Digitel, another Venezuelan mobile operator alternatively released the iPhone 4 to the Venezuelan market. At the moment there are contradictory versions about the additional "hotspot" service that allows to connect to the internet other additional computers through bluetooth, data cable or wireless WIFI network (see links 1 and 2).

The first thing that stands out is that while in countries such as: Belgium, Canada, Germany, Ecuador, Mexico, Germany, Russia, Spain, United Kingdom, among others, iPhone 4 and iPhone 3GS devices can be purchased without the so-called "simlock" (see link 3), in Venezuela none of the two carriers that promote iPhones offer this option. In some of the countries mentioned above, carriers are also obliged to unlock the devices after the end of the service contract.

## What is simlock? 
Simlock is a technique implemented by handset manufacturers so that handsets can only use SIM cards from a specific mobile operator. This technique is used to allow mobile operators to subsidize handsets to their users for the duration of a cell phone contract. In this way users will not be able to use the equipment with alternative mobile operators.

## What is the "hotspot" feature? 
The iPhone, like many other devices, allows you to share your data connection to the Internet through a technique called tethering. At first this technique was not accepted by mobile operators, mainly AT&T in the US, as it allowed users to connect to the Internet from a laptop via the iPhone. In this way many users managed to overload AT&T's data network in such a way that it did not work reliably. AT&T has been changing those contracts that granted unlimited data plans to its users to contracts with plans in which the connection speed is reduced if the user exceeds a certain amount of data per month.

The "hotspot" feature was officially introduced by Apple with iOS v4, although it had already been implemented using software that was installed using a technique called jailbreak.

## What is iOS?
iOS is the operating system for iDevices: iPhone, iPad, iPod Touch. At the moment the current version is 4.3.3 and Apple is testing the new generation called iOS 5.

## What is jailbreak? 
The jailbreak is a technique that inhibits the "trust-chain" so that programs that are not explicitly allowed by Apple can run on the iPhone. This way you can install programs that allow the hotspot function, programs to disable the simlock, among others. This method is not desired by Apple, on the contrary, in case a user implements it, he loses the warranty of his device. However, in the event that your device has a defect, you can reinstall the original Apple iOS on your device, and the company will not give you problems when performing warranty work. As for the legality of this method, the US supreme court ruled that it was completely legal in the US (link 7).

Having clarified these technical aspects, the big question is how to inhibit the simlock of my iPhone to be able to use any SIM (or micro-SIM) regardless of the mobile operator?

First of all we must clarify why we want an unlocked iPhone?
Surely many people will have different answers to these questions, however, I think the most important ones are:

- the freedom to choose from any cell phone service provider
- the ability to re-sell the device to another person using another cell phone provider
- the possibility to save costs abroad by using prepaid SIM cards in the USA, Europe and Asia.
the last option being the one that affects cell phone service providers the most since they charge exorbitant amounts for the so-called international roaming.

## How to unlock an iPhone?
The first option we have is through the so-called NCK, a code provided by Apple that is unique to each device. However this code is only provided by Apple, if the mobile operator agrees to do so. This is not the case in Venezuela, so there we have no possibility.
The second option is through software. In order to be able to do an unlock, first you have to jailbreak the device. Once the jailbreak is done, the user must install a program called ultrasn0w that manages to inject a cracking vector to the iPhone and thus inhibit the simlock (link 8 contains instructions for this method).
The third possibility is to make use of the so-called turbo-sims or gevey sims. This option includes the purchase of an additional sim adapter and in many cases requires a lot of patience.
Obviously the best way to do the unlock is through the first one. However, unfortunately we live in a country in which the political will is not in accordance with the interests of the people but in favor of big capital. In contrast to other countries, Venezuela does not have a legislation that forces mobile operators to disable the simlock once the contract is terminated (Note: I hope this comment reaches our legislators and they make a change in the legislation).

The second option represents a free alternative to unlock the iPhone thanks to a team of hackers called "dev-team" (link 5) who do this work for free, and publish the source code of their work under a free license: GPL.  The "dev-team" offers several programs that first of all jailbreak your iPhone: redsn0w and Pwnage Tool, and another one called untrasn0w that allows you to unlock your phone. Although the dev-team has done an outstanding job, so far the unlock only works with certain iOS versions and baseband. To date, the latest baseband version has not been unlocked.
It is important to highlight that the source code of these programs has been published! This ensures that many programmers have access to the source code and, in such a case, could fix bugs or notice if there are viruses or malicious code.

The third option is a sim adapter based option and works at that level. Because it is the most expensive option, and because Apple continually changes its technique for disabling these cards, this should be the last technique to be used. The supplier of these adapters is applenberry (link 6).

## What is the baseband?
The baseband is the software that controls the GSM chip of the iPhone. So far all un-locks offered by the "dev-team" exploited baseband programming errors in order to inject hacking vectors and disable the sim-lock. The latest iPhone 4 baseband could not be hacked. The dev-team is working on a way to hack this baseband.

## Recommendations
I have seen many people on mercadolibre.com.ve or on youtube offering their services, with exaggerated prices, to unlock your iPhone. In case you don't have a very up-to-date iOS it is quite possible that you can unlock your iPhone yourself at no additional cost.
Technical knowledge is not really necessary! On the following page you will find more information on how to unlock your iPhone and if your iPhone is eligible for this software solution: iClarified.

In case your iOS version is the most current and you cannot do a software unlock, the alternative is the gevey sim adapter. These are currently available for 150 BsF. at mercadolibre.com.ve.

---
## Links
- [http://support.apple.com/kb/HT1937?viewlocale=es_ES](http://support.apple.com/kb/HT1937?viewlocale=es_ES)
- [http://en.wikipedia.org/wiki/IPhone](http://en.wikipedia.org/wiki/IPhone)
- [http://theiphonewiki.com/wiki/index.php?title=Unlock](http://theiphonewiki.com/wiki/index.php?title=Unlock)
- [http://blog.iphone-dev.org/](http://blog.iphone-dev.org/)
- [http://applenberry.com/store/](http://applenberry.com/store/)
- [http://www.wired.com/threatlevel/2010/07/feds-ok-iphone-jailbreaking/](http://www.wired.com/threatlevel/2010/07/feds-ok-iphone-jailbreaking/)
- [http://iclarified.com/entries/index.php?caid=2&scid=11&seid=1](http://iclarified.com/entries/index.php?caid=2&scid=11&seid=1)