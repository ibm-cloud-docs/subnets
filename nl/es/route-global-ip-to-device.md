---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, Global IP addresses, Update button

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Direccionar una dirección IP global a un dispositivo
{:#route-global-ip-address-device}

El usuario direcciona manualmente las direcciones IP globales a cualquier dispositivo ofrecido por {{site.data.keyword.BluSoftlayer_notm}}. Para direccionar una IP global a un dispositivo, el dispositivo debe estar asociado con la cuenta que posee la IP global. Siga estos pasos para direccionar una dirección IP global a un dispositivo.

1. Navegue a la pantalla IP global en el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/). Consulte [Mostrar la pantalla IP global](/docs/infrastructure/subnets?topic=subnets-display-the-global-ip-screen){:new_window}.
* Seleccione la subred de IP global que va a direccionar.
* Comience a escribir la dirección IP del dispositivo al que se va a direccionar la IP global en el campo **Direcciona a**. Este campo se completa automáticamente en función de lo que escriba. Muestra cualquier dispositivo asociado con su cuenta.
* Indique las notas pertinentes sobre la IP global, el dispositivo u otros elementos en el campo **Notas**.
* Seleccione el botón **Actualizar** para completar el direccionamiento o seleccione **Cancelar** para cancelar la acción y volver a la pantalla **Subredes**.

## Qué sucede a continuación
{:#route-global-ip-address-device-next}

Cuando se inicia el direccionamiento de la subred de IP global, se inicia el proceso. Normalmente, los direccionamientos tardan menos de un minuto en completarse. En cualquier momento, se puede [cancelar el direccionamiento](/docs/infrastructure/subnets?topic=subnets-unroute-a-global-ip-address-from-a-device) de la IP global al dispositivo.
