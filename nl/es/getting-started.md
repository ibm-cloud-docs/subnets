---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Iniciación a las subredes y las IP

En cualquier momento, los clientes de IBM Cloud pueden solicitar subredes estáticas, subredes portátiles públicas y privadas o subredes globales que constan de direcciones IPv4 e IPv6. 

Para solicitar subredes e IP:

1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com/){: new_window} e inicie sesión en su cuenta.
2. En la navegación del portal de clientes, seleccione **Red > Gestión de IP > Subredes**.
3. Para iniciar el proceso de pedido, seleccione el tipo adecuado de subred desde el menú desplegable. 

**Tenga en cuenta que las subredes se crean para los clientes caso por caso, lo que implica un proceso de selección que tiene en cuenta la proporción entre IP y servidores.**

## Bloques de IP estáticos y portátiles
{{site.data.keyword.BluSoftlayer_notm}} ofrece actualmente 2 tipos diferentes de bloques de IP: estáticos o portátiles. Están diseñados para utilizarse de diferentes maneras. A continuación, se muestra una breve descripción de cada tipo de bloque, y se incluye también una sección sobre el uso de estas direcciones IP dentro de una máquina virtual.
 
### Bloque de IP estático
El tipo de bloque de IP más utilizado dentro de la red de {{site.data.keyword.BluSoftlayer_notm}} es el bloque de IP estático. Los bloques de IP estáticos se direccionan directamente a una IP específica en nuestra red. Todas las direcciones IP de un bloque estático se pueden utilizar en el servidor. Una de las ventajas principales de utilizar un bloque de IP estático es que no se pierden las dos primeras y las dos últimas direcciones IP, sino que se pueden utilizar todas las direcciones del bloque. 

A continuación, se muestra un ejemplo de un bloque de IP estático pequeño (192.168.0.4/30), en el que las 4 IP de este bloque están disponibles para el servidor:
```
·192.168.0.4 – Usable Address
·192.168.0.5 – Usable Address
·192.168.0.6 – Usable Address
·192.168.0.7 – Usable Address
```
Con un bloque portátil, realmente solo se podría utilizar una única dirección IP de este bloque en el servidor, porque las direcciones IP de difusión, red y pasarela están vinculadas directamente a la VLAN.  

Nota: hay una técnica especial que permite utilizar todas las IP, porque con la máscara de subred asignada sólo se pueden utilizar todas menos una (la IP de difusión). Para utilizar todas las IP, utilice la máscara de subred de 255.255.255.255, en lugar de perder la IP de difusión.

### Bloque de IP portátil
Los bloques de IP portátiles se pueden utilizar en varios servidores dentro de una sola VLAN simultáneamente. Ofrecemos dos tipos diferentes de bloques de IP portátiles:

 * El primer tipo de bloque de IP portátil es un bloque "direccionado a VLAN". Se trata de un bloque de IP estático que se direcciona a toda una VLAN en lugar de a una dirección IP específica.
 * El otro tipo de IP portátil es un bloque "secundario en VLAN", que está diseñado para ser utilizado en un entorno virtual.
 
La diferencia principal entre los dos es el número de IP que están disponibles para su uso. 

Los **bloques direccionados a VLAN**, como un bloque estático, proporcionan acceso a todas las IP incluidas en el bloque. Sin embargo, los bloques **secundarios en VLAN**, requieren que las IP de difusión, red y pasarela estén enlazadas directamente a la VLAN, lo que las presenta como no utilizables. Los bloques **direccionados a VLAN** se utilizan cuando el usuario desea utilizar cualquier IP incluida en el bloque en cualquier servidor de dentro de la VLAN, en cualquier momento. Los bloques **secundarios en VLAN**, se utilizan junto con una máquina virtual. En la sección _IP para máquinas virtuales_ se proporciona más información sobre los bloques **secundarios en VLAN**.

De forma predeterminada, al solicitar un bloque de IP portátil, {{site.data.keyword.BluSoftlayer_notm}} le proporcionará un bloque **secundario en VLAN**. Si desea convertir este bloque en un bloque **direccionado a VLAN** para utilizarlo con los servidores dentro de una sola VLAN, abra una incidencia de soporte para solicitar que este bloque se convierta en un bloque **direccionado a VLAN**.

### POD compatibles con HSRP (Hot Standby Router Protocol)

Es importante mencionar que los POD que emplean HSRP (Hot Standby Router Protocol) utilizan 2 direcciones IPv4 adicionales: una para la interfaz de VLAN de cada direccionador participante y otra para cada bloque **secundario en VLAN** configurado en la VLAN. La mayoría de nuestros POD son compatibles con HSRP.

A continuación, se muestra un ejemplo de un bloque **secundario en VLAN** (192.168.0.4/28) que se utiliza para varias máquinas virtuales en un POD HRSP.
```
192.168.0.0 –  Network Address
192.168.0.1 –  Gateway Address
192.168.0.2 –  Router A Vlan Interface
192.168.0.3 –  Router B Vlan Interface
192.168.0.4 –  VPS1
192.168.0.5 –  VPS2
192.168.0.6 –  VPS3
192.168.0.8 –  VPS4
192.168.0.9 –  VPS5
192.168.0.10 – VPS6
192.168.0.11 – VPS7
192.168.0.12 – VPS8
192.168.0.13 – VPS9
192.168.0.14 – VPS10
192.168.0.15 – Broadcast Address
```
 
### IP para máquinas virtuales
Las máquinas virtuales (VM) se suelen utilizar en las cargas de trabajo en nube, a veces denominadas "instancias" o "cálculos". Esta sección proporciona información sobre qué tipo de bloques de IP son necesarios para utilizar en una VM. La información proporcionada aquí se basa en Microsoft Hyper-V.

Cada VM conectada a la red de {{site.data.keyword.BluSoftlayer_notm}} en un entorno virtual requiere una dirección IP primaria de un bloque portátil de direcciones IP, porque Hyper-V requiere que cada VM proporcione una dirección de difusión, red y pasarela en la misma subred que la IP primaria asignada a dicha VM. Una de las ventajas para nuestra configuración de red es que se puede utilizar un único bloque **secundario en VLAN** para varias máquinas virtuales. 

A continuación, se muestra un ejemplo de un bloque **secundario en VLAN** (192.168.0.4/29) que se utiliza para varias máquinas virtuales:
```
·192.168.0.0 – Network Address
·192.168.0.1 – Gateway Address
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Broadcast Address
```
Tal como muestra el ejemplo, este bloque **secundario en VLAN** proporciona 5 direcciones IP utilizables de las 8 direcciones IP del bloque, vinculadas a través de 3 máquinas virtuales diferentes. Esta configuración plantea la pregunta: "¿cómo puedo añadir más IP a una máquina virtual si están utilizadas todas las IP del bloque portátil?". Este problema se puede resolver utilizando un bloque estático o un bloque portátil **direccionado a VLAN**.

Para utilizar un bloque estático dentro de una VM, solicite un nuevo bloque de IP estático desde el Portal de clientes. Durante el pedido de este bloque, puede seleccionar la dirección IP a la que desea que se direccione este bloque. Al seleccionar la dirección IP que se asigna a la VM, el nuevo bloque se direccionará específicamente a dicha VM. De este modo, puede enlazar el nuevo bloque de IP directamente a la VM y empezar a utilizarlas inmediatamente.

Como alternativa, si desea que el nuevo bloque se pueda utilizar en más de una máquina virtual, utilice un bloque **direccionado a VLAN**. Los bloques **direccionados a VLAN** están disponibles comprando un bloque de IP portátil desde el portal y seleccionando la VLAN en la que reside la dirección IP de la VM. Una vez creado el bloque de IP, estará disponible para su uso en cualquier servidor o VM de dicha VLAN.
