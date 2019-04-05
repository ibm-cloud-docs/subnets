---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Addresses, Global IP address, single IP address

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Acerca de las direcciones IP globales
{:#about-global-ip-address}

Una dirección IP global es una Subred Secundaria Estática especializada. Se le entrega como una subred /32 (en otras palabras, una dirección IP única) que se puede direccionar a cualquier otra dirección IP de su cuenta. Hay tanto direcciones IPv4 como IPv6 disponibles y cada tipo debe ser direccionada a una dirección IP con la misma versión de IP. Los destinos de direccionamiento aceptables incluyen direcciones IP primarias utilizadas por los servidores y cualquier dirección IP de subred secundaria portátil. Las funciones exclusivas de una dirección IP global son las siguientes:

  * Direccionamiento bajo demanda a direcciones IP de una cuenta, de forma global.
  * La dirección se anuncia a Internet por parte de todos los direccionadores de extremo de {{site.data.keyword.cloud}}. Por lo tanto, los datos toman la vía de acceso más corta a la red de {{site.data.keyword.cloud}}, y desde allí puede utilizar la red troncal dedicada y global de {{site.data.keyword.cloud}} para llegar al destino que ha configurado.

Las direcciones IP globales proporcionan flexibilidad. Le permiten desplazar cargas de trabajo entre servidores, incluso a través de centros de datos geográficamente dispares. Además, las direcciones IP globales proporcionan persistencia de IP al permitir transiciones sin necesidad de adaptación (por ejemplo, para evitar las memorias caché de DNS). La capacidad de direccionamiento global es perfecta para realizar la transición de cargas de trabajo entre sitios de recuperación tras desastre, o para realizar una transición sin interrupciones a un nuevo despliegue en un área geográfica que pueda dar un mejor servicio a la audiencia.

| **Disponibilidad** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Red pública   | Sí  | Sí  |
| Red privada  |      |      |


## Gestión de direcciones IP globales
{:#manage-global-ip-address}

Para gestionar direcciones IP globales, siga estos pasos:

 1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/){: new_window} e inicie sesión en su cuenta.
 1. En la navegación del portal de clientes, seleccione **Infraestructura clásica**.
 1. En el menú de navegación de Infraestructura clásica, seleccione **Red > Gestión de IP > IP global**.
 1. Verá una lista con sus direcciones IP globales. Utilice filtros para limitar la búsqueda según sea necesario. 
 
Puede observar que algunas entradas no tienen un valor en **Destino**, lo que indica que la dirección IP global IP no está direccionada actualmente, por lo que no está en servicio.

### Direcciones de direccionamiento y desdireccionamiento
{:#route-unroute-address}

Una vez que localice la dirección IP global deseada, haga clic en su identificador de subred. A continuación, verá una pantalla que muestra su destino de ruta actual, si es aplicable. Para direccionar (enviar tráfico) a un nuevo destino, tiene dos opciones:

 * especificar una dirección IP completa, o
 * empezar a escribir un nombre de host
 
Escribir un nombre de host le permite buscar el nombre de host de un servidor, por lo que puede buscar su dirección IP. Después de especificar una dirección IP, seleccione **Actualizar**. Para desdireccionar la dirección IP global, seleccione **Borrar**. Cuando el estado de entrada cambia a 'No direccionado', seleccione **Actualizar**.

El menú desplegable no es una lista exhaustiva de direcciones IP disponibles. Puede especificar manualmente la dirección IP deseada si no aparece en la lista de selección.
{:note}

### ¿Con qué frecuencia puedo actualizar?
{:#how-often-can-i-update}

Únicamente se permite que se una actualización de una ruta en curso en un momento dado. Si intenta actualizar la ruta de una dirección IP global mientras hay otra actualización en curso, recibirá un error. Espere a que la actualización anterior se haya completado para volver a intentarlo.


## Cómo ordenar direcciones IP globales
{:#how-to-order-global-ip-address}

Siga estas instrucciones para ordenar las direcciones IP globales:

  1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/){: new_window} e inicie sesión en su cuenta.
  1. En la navegación del portal de clientes, seleccione **Infraestructura clásica**.
  1. En el menú de navegación de Infraestructura clásica, seleccione **Red > Gestión de IP > IP global**.
  3. Pulse el enlace **Direcciones IP nuevas**.
  4. En el menú desplegable, seleccione **IPv4 global** o **IPv6 global**, según sea necesario, y pulse **Continuar** para iniciar el proceso de pedido.

![Figura 1](images/1_2.png)

### ¿Qué sucede a continuación?
{:#global-ip-address-next}

Una vez superados los procesos de aprobación necesarios según el estado de su cuenta, al cabo de unos minutos aparecerá en su cuenta una nueva subred de IP global.

### Límite de recursos
{:#global-ip-resource-limit}

Una cuenta sólo puede tener cinco (5) direcciones IP globales por versión de IP. Por ejemplo, cinco (5) direcciones IP globales de IPv4 y cinco (5) direcciones IP globales de IPv6.

## Cómo cancelar las direcciones IP globales
{:#how-to-cancel-global-ip-address}

Si ya no necesita una dirección IP global, siga estos pasos para cancelarla:

  1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/){: new_window} e inicie sesión en su cuenta.
  1. En la navegación del portal de clientes, seleccione **Infraestructura clásica**.
  1. En el menú de navegación de Infraestructura clásica, seleccione **Red > Gestión de IP > IP global**.
  1. Complete los filtros necesarios para localizar la dirección deseada.
  1. A la derecha de la de la entrada de la dirección en la lista de direcciones, se muestra un círculo con una X. Pulse en este icono para iniciar el proceso de cancelación.
