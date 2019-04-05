---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: IP addresses, IPs Subnets, types of subnets

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Iniciación a las subredes y las IP
{:#getting-started-subnets-ips}

Las subredes son una parte importante de cómo se utiliza internet, y esto es también así cuando se utiliza {{site.data.keyword.cloud}}. Tenemos terminología específica para los tipos y usos de las subredes que se encuentran en nuestra plataforma. Cada subred proporciona direcciones IP a los recursos de formas distintos. Encontrará los siguientes tipos de subredes, y al saber más sobre cada tipo de subred, podrá comprender cómo utilizarlas mejor en su infraestructura de nube.

  * Subredes primarias - Subredes asignadas para satisfacer las necesidades de direcciones IP de otros productos, como por ejemplo servidores Bare Metal o instancias de servidor virtual. Estas subredes se asignan y se eliminan de forma automática.
  * Subredes secundarias - Subredes que ha adquirido y direccionado usted; y que se cancelan cuando ya no son necesarias. Hay dos subtipos:
    * Portátiles - Las direcciones IP están disponibles para todos los recursos de una VLAN.
    * Estáticas - Las direcciones IP están disponibles para el recurso identificado como punto final de direccionamiento.
  * Direcciones IP globales - Comportamiento de direccionamiento exclusivo que utiliza la estructura de la red troncal de {{site.data.keyword.cloud}}, que proporciona direcciones IP al recurso identificado como punto final de direccionamiento.

Revise cada tipo de detalle en [Acerca de las subredes y las IP](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) para revisar aspectos como, por ejemplo, IPv4 frente a IPv6 y la disponibilidad de la red pública/privada.

Para comprender mejor las subredes y su uso en general, consulte [Subred ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://en.wikipedia.org/wiki/Subnetwork).
Además, verá que nos referimos a las subredes utilizando la [notación CIDR ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


## Solicitar las subredes
{:#ordering-subnets}

Siga estos pasos para solicitar subredes, que proporcionan direcciones IP adicionales:

  1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/){: new_window} e inicie sesión en su cuenta.
  1. En la navegación del portal de clientes, seleccione **Infraestructura clásica**. 
  1. En la navegación de Infraestructura clásica, seleccione **Red > Gestión de IP > Subredes**.
  1. Seleccione el enlace, "Nuevas direcciones IP", en la parte superior derecha de la lista.
  1. Para iniciar el proceso de pedido, seleccione el tipo de subred Pública o Privada en los botones de selección.
  1. Elija entre las opciones IPv4 o IPv6.
  1. Para elegir IP estáticas o globales, haga clic en el recuadro correspondiente. 
    1. Para IPv4, utilice la lista desplegable disponible en las opciones Estática o Portátil para elegir cuántas direcciones desea. 
  1. Seleccione la VLAN para establecer dónde se direccionarán las nuevas direcciones IP.
  1. Complete el resto de información que se solicita y pulse **Crear**.


Una vez que se ha adquirido una subred, el tipo y el destino de direccionamiento no se pueden cambiar. Debe solicitar una nueva subred para adquirir un tipo de subred distinto o un punto final de direccionamiento diferente.

### ¿Qué sucede a continuación?
{:#ordering-subnets-next}

Una vez superados los procesos de aprobación necesarios según el estado de su cuenta, al cabo de unos minutos aparecerá en su cuenta una subred con la configuración deseada.
