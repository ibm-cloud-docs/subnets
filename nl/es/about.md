---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-04"

keywords: IP addresses , IP address, duration of your use

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Acerca de subredes e IP
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} tiene terminología específica para los tipos y usos de las subredes que se encuentran en nuestra plataforma. Conocer su uso previsto le ayudará a conocer la mejor manera de usarlos en su infraestructura de nube.


## Tipos de subredes
{:#subnet-types}

### Subredes primarias
{:#primary-subnets}

Las subredes primarias las asigna automáticamente {{site.data.keyword.BluSoftlayer_notm}}, y son las que proporcionan direcciones IP a los recursos según se necesitan. Asignamos y eliminamos Subredes Primarias según sea las necesidades para el cumplimiento de otros productos. Todos los servidores se suministrarán con al menos una dirección IP de una subred primaria, que se conoce comúnmente como dirección IP primaria. Algunos productos y opciones dan hacen que se asignen más direcciones IP primarias.

Es importante entender que las direcciones IP dentro de las subredes primarias, que aún no están asignadas a recursos, no están disponibles para su uso. Si intenta utilizar direcciones IP de las subredes primarias sin asignar, inevitablemente las asignaremos a otro recurso en algún momento. Esto da lugar a conflictos de IP en la red y a la interrupción del servicio general. Nos reservamos el derecho de bloquear o dejar inutilizable de algún otro modo cualquier dirección IP de una Subred Primaria que no se haya asignado específicamente durante el cumplimiento de otros productos.

Se **recomienda** utilizar **Subredes secundarias** como direcciones IP de servicio/aplicación externas; especialmente al diseñar aplicaciones de varios servidores. Utilizar las direcciones IP primarias asignadas a los servidores es correcto. Sin embargo, no tiene la flexibilidad de mantener las direcciones conocidas a los servicios que son neutros a la cancelación y solicitud de servidores. No se garantiza nada con respecto al orden en que se asignan las direcciones IP primarias, por ejemplo ascendente, descendente, omitiendo lagunas, etc.

Bajo ninguna circunstancia podemos reservar direcciones IP en Subredes Primarias para usted.
{:note}

### Subredes secundarias
{:#secondary-subnets}

Las subredes secundarias proporcionan direcciones IP adicionales para muchas necesidades. A diferencia de las subredes primarias, estas subredes son propiedad suya durante todo el tiempo que la sutilice, y no se eliminarán a menos que las cancele. Se deben utilizar subredes secundarias cuando se necesite una dirección IP estable que no dependa de ningún dispositivo de cálculo específico. A continuación se indican algunos ejemplos de uso:

  * Direcciones IP que se pueden asignar a las máquinas virtuales locales y propias.
  * Varias direcciones IP de servicio distintas alojadas en un único servidor, lo que permite identificar fácilmente el tráfico. Se utiliza a menudo con servidores web y TLS.
  * Una dirección IP de servicio vinculada a DNS. Evite los retrasos en la memoria caché de DNS al cambiar las cargas de trabajo a los nuevos servidores (es decir la IP de servicio no cambiará simplemente porque la dirección IP primaria de un servidor lo haga)..
  * Configuraciones de alta disponibilidad que utilizan protocolos de direcciones IP "flotantes".

Para conseguir estos usos, y muchos más, ofrecemos diferentes opciones de direccionamiento para las subredes secundarias. Con el fin de ilustrar las diferencias entre las subredes secundarias que ofrecemos, nos referiremos a la subred de ejemplo siguiente en las explicaciones subsiguientes.

A continuación, se muestra un ejemplo de las direcciones IP proporcionadas por la subred 10.0.0.0/29:
```
10.0.0.0
10.0.0.1
10.0.0.2
10.0.0.3
10.0.0.4
10.0.0.5
10.0.0.6
10.0.0.7
```

#### Subredes estáticas
{:#static-subnets}

Una subred estática proporciona un único destino con acceso a todas las direcciones IP definidas por dicha subred. Una ventaja de utilizar una subred estática es que el dispositivo de destino puede utilizar todas las direcciones IP definidas; sin sufrir la penalización de uso habitual, de red, pasarela y difusión de direcciones. Así pues, si se utiliza nuestra subred de ejemplo, todas las direcciones son utilizables:

```
10.0.0.0 - Utilizable por un dispositivo
10.0.0.1 - Utilizable por un dispositivo
10.0.0.2 - Utilizable por un dispositivo
10.0.0.3 - Utilizable por un dispositivo
10.0.0.4 - Utilizable por un dispositivo
10.0.0.5 - Utilizable por un dispositivo
10.0.0.6 - Utilizable por un dispositivo
10.0.0.7 - Utilizable por un dispositivo
```

Por lo tanto, si un servidor tiene la dirección IP 10.0.0.13, y ha direccionado 10.0.0.0/30 estáticamente a 10.0.0.13, ese servidor ahora puede enlazar cuatro direcciones IP adicionales; recibiendo tráfico en cada una de forma individual. Es importante comprender que no se está realizando ninguna conversión de direcciones de red (NAT) para ninguna de las direcciones proporcionadas. Cada dirección se puede utilizar de forma nativa en servidores y, por lo tanto, cada una de ellas se puede utilizar para fines distintos.

| **Disponibilidad** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Red pública   | Sí  | Sí  |
| Red privada  |      |      |

#### Subred portátil
{:#portable-subnet}

Una subred portátil proporciona sus direcciones IP a todos los recursos de una VLAN. Esto significa que cualquier recurso de cálculo de la misma VLAN puede utilizar cualquier dirección proporcionada por la subred. Este comportamiento es muy útil para las direcciones "flotantes" entre varios recursos y desacopla la subred de un recurso concreto. Una necesidad de las subredes portátiles es que no todas las direcciones IP definidas por la subred son utilizables por dispositivos. La mecánica de redes requiere consumir algunas de las direcciones IP. Estas direcciones consumidas se conocen como las direcciones IP de difusión, de red y de pasarela. Observe las direcciones que están disponibles en nuestro ejemplo:

```
10.0.0.0 - Red
10.0.0.1 - Pasarela
10.0.0.2 - Utilizable por dispositivos
10.0.0.3 - Utilizable por dispositivos
10.0.0.4 - Utilizable por dispositivos
10.0.0.5 - Utilizable por dispositivos
10.0.0.6 - Utilizable por dispositivos
10.0.0.7 - Difusión
```

| **Disponibilidad** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Red pública   | Sí  | Sí  |
| Red privada  | Sí  |      |


### Direcciones IP globales
{:#global-ip-addresses}

Para obtener información sobre la oferta de IP globales, consulte la [documentación sobre IP globales](/docs/infrastructure/subnets?topic=subnets-about-global-ip-addresses).

| **Disponibilidad** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Red pública   | Sí  | Sí  |
| Red privada  |      |      |


## Cancelación de subredes
{:#canceling-subnets}

Si ya no necesita una subred secundaria, siga estos pasos para cancelarla:

  1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/){: new_window} e inicie sesión en su cuenta.
  1. En la navegación del portal de clientes, seleccione **Infraestructura clásica**. 
  1. En el menú de navegación de Infraestructura clásica, seleccione **Red > Gestión de IP > Subredes**.
  1. Elija los filtros que desee para localizar la subred deseada.
  1. En la parte derecha de la entrada de la subred, en la lista de subredes, se mostrará un círculo rojo con una X. Pulse en este icono para iniciar el proceso de cancelación.


## Consideraciones específicas del producto al solicitar subredes
{:#product-specific-considerations-subnets}

### Cortafuegos de hardware (compartido)
{:#hardware-firewall-subnets}

Las subredes portátiles no están protegidas por cortafuegos de forma predeterminada. Si necesita esta función, póngase en contacto con el representante de ventas. Las subredes secundarias mayores de /29 no se pueden direccionar a través de esta oferta de cortafuegos.

### Transferencia de direcciones IP de subred portátiles entre servidores
{:#transferring-portable-subnet-ip-between-servers}

Al transferir una dirección IP de un servidor a otro, asegúrese de que se ha enviado un paquete de ARP gratuito. Esto permite a nuestros direccionadores actualizar su entrada ARP y reenviar tráfico al servidor correcto. De no hacerlo, podría producirse un retraso de 4 horas en el nuevo servidor que recibe el tráfico para la dirección transferida.

### Dispositivos de direccionador virtual
{:#virtual-router-appliances-subnets}

Al solicitar subredes para una VLAN detrás de un dispositivo de direccionador virtual de alta disponibilidad, asegúrese de que la subred se ha configurado correctamente para permitir la migración tras error entre los dos dispositivos. Dispone de ayuda detallada en la documentación de [Configuración de alta disponibilidad de VRA](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
