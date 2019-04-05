---
copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, unroute process, Device Global IP addresses

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Cancelar el direccionamiento de una dirección IP global a un dispositivo
{:#unroute-global-ip-address}

En cualquier momento, el usuario puede cancelar manualmente el direccionamiento de las direcciones IP globales. Siga estos pasos para cancelar el direccionamiento de una dirección IP global a un dispositivo.

1. Navegue a la pantalla IP global en el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/). Consulte [Mostrar la pantalla IP global](/docs/infrastructure/subnets?topic=subnets-display-the-global-ip-screen){:new_window}.
* Seleccione la dirección IP global de la que va a cancelar el direccionamiento.
* Seleccione el botón **Borrar**.
* Seleccione el botón **Actualizar** para completar el proceso de cancelación del direccionamiento o seleccione **Cancelar** para cancelar la acción y volver a la pantalla **Subredes**.

## Qué sucede a continuación
{:#unroute-global-ip-next}

Una vez que se cancela el direccionamiento de una IP global a un dispositivo, la IP global ya no está asociada con ese dispositivo. Cuando finaliza el proceso de cancelación del direccionamiento de la IP global, dicha dirección IP global se puede [volver a direccionar](/docs/infrastructure/subnets?topic=subnets-route-a-global-ip-address-to-a-device) a cualquier otro dispositivo de la cuenta.
