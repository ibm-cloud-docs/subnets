---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Acerca de subredes e IP

IBM Cloud proporciona una serie de opciones para solicitar subredes y direcciones IP, de modo que pueda diseñar una infraestructura que responda a sus necesidades. Entender cómo funcionan las subredes y conocer sus casos de uso previsto le ayudará a lograr exactamente lo que necesita.

## Tipos de subredes

Al saber más sobre cada tipo de subred, puede entender cómo utilizarlas mejor en la infraestructura de nube.

### Subredes primarias

{{site.data.keyword.BluSoftlayer_notm}} asigna automáticamente las subredes primarias en las VLAN, con el fin de prestar servicios y un suministro automatizado en las VLAN. Estas subredes no están disponibles para los servicios o las direcciones IP secundarias, porque las usan nuestros sistemas automatizados. Las subredes primarias se asignan a nuevos servidores automáticamente. Si intenta utilizarlas en los servidores, puede provocar un conflicto de direcciones IP, en cuyo caso deberá eliminar la dirección IP.

**Nota: no se pueden reservar direcciones IP en subredes primarias para su uso.**

### Subredes portátiles

Las subredes portátiles se pueden pedir mediante el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com/) Estas subredes suelen proporcionar direcciones de máquina virtual (VM) o direcciones IP secundarias en servidores o interfaces secundarias. Estas subredes también se pueden utilizar para direcciones IP de HA o clúster, porque nuestros direccionadores las rastrean mediante ARP. Se pueden trasladar con facilidad. El formato estándar de estas subredes incluye su propia dirección de difusión, red, y pasarela, lo que permite utilizar inmediatamente tres de sus direcciones IP.

### Subredes estáticas

Las subredes estáticas son otro tipo de subred que puede solicitar a través del [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com/network/subnets/order). Las subredes estáticas normalmente se utilizan para servidores web, correo electrónico u otros servicios alojados en un servidor, lo que requiere varias direcciones IP adicionales para permitir las conexiones. Las subredes estáticas son exclusivas, porque se debe especificar otra dirección IP existente que ya esté asignada a un servidor al que se direcciona directamente la subred. Tiene la flexibilidad de direccionar la subred como desee y puede trasladarla a distintos servidores, pero para ello debe cambiar la ubicación direccionada.

### Direcciones IP globales

Para obtener información sobre la oferta de IP globales, consulte la [documentación sobre IP globales](about-global-ip.html).

## Consideraciones a tener en cuenta con diferentes subredes

### Cortafuegos de hardware

Las subredes portátiles no están protegidas por cortafuegos de forma predeterminada. Si necesita esta función, póngase en contacto con el representante de ventas. Las subredes que necesiten protección no pueden superar una subred /29.

### Transferencia de IP portátiles entre servidores

Al transferir una dirección IP portátil de un servidor a otro, asegúrese de que se envíe un paquete ARP gratuito, de forma que nuestros direccionadores puedan actualizar la entrada ARP y reenviar de la dirección IP actualizada al servidor correcto. Si no envía el paquete ARP, la dirección IP puede tardar 4 horas o más en empezar a responder correctamente.

### Pasarelas Vyatta

Al solicitar subredes para una VLAN situada detrás de una pasarela Vyatta, asegúrese de que la subred se haya añadido correctamente a la configuración de Vyatta. Si utiliza VRRP para HA, asegúrese de que la subred se haya configurado correctamente para permitir la migración tras error entre los dos dispositivos de pasarela. Si necesita más ayuda con estas tareas, consulte estos dos artículos sobre la configuración de la pasarela Vyatta:

 * [Dispositivos de pasarela de red Vyatta](../network-gateways/network-gateway-devices-vyatta.html)

 * [Configuración de alta disponibilidad de Vyatta](../vyatta/vyatta-high-availability-configuration.html)
 
 ### Cancelación de subredes
 
Las subredes que se asignan automáticamente a una cuenta para la realización de pedidos de dispositivo están sujetas a reclamaciones automáticas cuando se dejan de hacer referencia a ellas. Las subredes que se piden por separado se pueden cancelar en cualquier momento.
