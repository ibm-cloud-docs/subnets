---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Primary IP, IP address, subnet's IP

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}
{:faq: data-hd-content-type='faq'}

# Preguntas más frecuentes
{:#subnets-faq}

## ¿Qué significa `IP primaria sólo para servidor futuro` cuando miro las direcciones IP de una subred?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

{{site.data.keyword.BluSoftlayer_notm}} asigna y elimina las subredes primarias según las necesidades para los otros recursos que ha solicitado, como por ejemplo servidores Bare Metal o instancias de servidor virtual. No asignamos simplemente una dirección IP cada vez, asignamos una subred. Esto significa que a veces hay espacio adicional para los recursos futuros. Esta designación indica que estas direcciones serán utilizadas por los recursos futuros. Consulte la pregunta, "**¿Puedo utilizar las otras direcciones IP definidas por las subredes primarias que veo?**" para saber por qué no debe considerar utilizables estas direcciones IP.


## ¿Puedo utilizar las otras direcciones IP definidas por las subredes primarias que veo?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

¡No! Nos damos cuenta de que ve las subredes primarias que asigna {{site.data.keyword.BluSoftlayer_notm}} como cualquier otra subred, pero tal como se describe en [Acerca de las subredes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), las subredes primarias son las que proporcionan direcciones IP a los recursos bajo demanda. Asignamos y eliminamos Subredes Primarias, según se necesitan para cumplir con otros productos. Si intenta utilizar direcciones IP de las subredes primarias sin asignar, inevitablemente las asignaremos a otro recurso en algún momento. Esto da lugar a conflictos de IP en la red y a la interrupción del servicio general. Nos reservamos el derecho de bloquear o dejar inutilizable de algún otro modo cualquier dirección IP de una Subred Primaria que no se haya asignado específicamente durante el cumplimiento de otros productos. Debe utilizar **Subredes secundarias** para todas las necesidades adicionales de direcciones IP, y se recomienda utilizarlas para las direcciones de aplicación/servicio. Las subredes secundarias son mucho más flexibles y se mantienen en su cuenta mientras sea propietario de ellas.


## ¿Hay alguna forma de especificar qué subred quiero utilizar para mi dispositivo cuando hago el pedido?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

Sí, se puede especificar una subred específica durante el proceso de pedido. Al hacer un pedido de un dispositivo, esta opción estará disponible al final del formulario de pedido. Después de seleccionar una VLAN privada, se presenta una lista de subredes primarias direccionadas a dicha VLAN. Puede seleccionar una subred deseada. Se puede repetir el mismo proceso para la VLAN pública y la subred.

Es importante tener en cuenta que el envío del pedido **no garantiza** que una dirección IP esté disponible en la subred solicitada. Si no hay direcciones disponibles, contactará con usted con el fin de determinar las medidas a tomar. Para una mejor experiencia con {{site.data.keyword.BluSoftlayer_notm}}, se desaconseja seleccionar una subred para los usos típicos.


## Me he quedado sin direcciones IP, ¿qué hago?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

¡Esto no va a suceder! Asignamos automáticamente subredes primarias poner a su disposición más direcciones IP para realizar sus compras de cálculo. No tiene que gestionar nada. No obstante, si quiere decir que necesita más direcciones IP para, por ejemplo, máquinas virtuales locales o para segregar aplicaciones, consulte **Subredes secundarias** en [Acerca de las subredes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).


## ¿Cómo puedo asignar más direcciones IP a un recurso de cálculo?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

En primer lugar, deberá adquirir una **Subred secundaria**. Las hay de varios tipos, por lo que debería consultar [Acerca de las subredes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips). Una vez que tenga una subred direccionada a la dirección IP o a la VLAN deseada, deberá consultar la documentación de cálculo específica para saber cómo configurar las nuevas direcciones IP:

  * [Asignación de direcciones IP de servidor Bare Metal](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Asignación de direcciones IP de instancia de servidor virtual](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## ¿Qué significa `Reservado para HSRP` en las direcciones IP de una subred?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

En un número decreciente de ubicaciones, {{site.data.keyword.BluSoftlayer_notm}} tiene direccionadores que utilizan una técnica conocida como Hot Standby Router Protocol o HSRP. Concretamente, la forma en que se utiliza tiene un impacto en las direcciones IP disponibles para las ***Subredes secundarias portátiles***; lo que significa que perderá el acceso a dos direcciones adicionales en estas ubicaciones. Como indica la designación, "Reservado para HSRP", estas direcciones IP se reservan para cumplir las necesidades de HSRP. Incluso puede tener subredes en el mismo direccionador, algunas con direcciones reservadas y algunas sin. Al igual que con cualquier conflicto de IP, no intente utilizar estas direcciones o puede afectar al tráfico en toda la subred.

