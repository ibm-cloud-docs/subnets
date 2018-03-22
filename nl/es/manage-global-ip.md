---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Gestionar direcciones IP globales

Puede gestionar sus direcciones IP globales en la pantalla **Subredes**. 

1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com/){: new_window} e inicie sesión en su cuenta.
2. En la navegación del portal de clientes, seleccione **Red > Gestión de IP > Subredes**.
3. En el menú desplegable, seleccione **IPv4 global** (o IPv6) para filtrar la lista de subredes para mostrar solo las IP globales.
4. Pulse la IP global que desea gestionar.
 
  **Nota: una dirección IP global es una dirección IP estática que se puede direccionar a cualquier servidor dentro de la red de IBM Cloud. La oferta actual de direcciones IP estáticas solo se puede direccionar a una dirección IP dentro del mismo centro de datos, pero esta restricción no se aplica a las direcciones IP globales.**

5. En la página de gestión de direcciones IP, escriba la dirección IP del servidor al que desea direccionar la dirección IP global, especifique las notas aplicables y, a continuación, seleccione **Actualizar**.

![Figura 2](images/2_1.png)

## Añadir una IP global al servidor 

Antes de que el servidor acepte tráfico para la IP global, esta se debe añadir correctamente al sistema. Cada sistema necesita mandatos ligeramente diferentes, que se muestran en las secciones siguientes.

### Para servidores Linux:

**Red Hat/CentOS**

1. Edite (vim o nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* Añada las líneas siguientes:
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. Edite `/etc/network/interfaces`

* Añada las líneas siguientes:

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

Si el sistema no funciona correctamente, añada las líneas siguientes y sustituya # con el siguiente número disponible:

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### Para servidores Windows

1. Vaya a: **Inicio -> Panel de control -> Conexiones de red -> Conexión de área local (pública) (propiedades)**.
* Seleccione: **Protocolo de Internet (TCP/IP)** y pulse **Propiedades -> Avanzadas**.
* Seleccione **Añadir** en la sección de direcciones IP e indique la dirección IP y la máscara de subred.
* Una vez realizada esta tarea, pulse "Aceptar" para volver al escritorio.

Para verificar que se han aplicado los valores, abra un indicador de DOS navegando a **Inicio -> Ejecutar -> "cmd"** y ejecute el mandato

```
        > ipconfig /all
```

**Notas:**

* Si ya tiene un archivo `eth1:1` en el servidor como en el ejemplo anterior, aumente el último dígito al siguiente entero disponible.
* La modificación de una dirección IP global a un nuevo servidor o VSI tarda hasta cinco minutos en aplicarse. 
* Dentro de la red de IBM Cloud, el cambio de direccionamiento tarda menos de 1 minuto en actualizarse.
* Las IP globales no funcionan para equilibradores de carga local.
* Las IP globales se distribuyen desde una subred exclusiva; las IP de cliente existentes no se pueden convertir en IP globales ni utilizarse como tales.
* Por sí mismas, las IP globales no suponen una solución de migración tras error automática, porque carecen de comprobaciones de estado; sin embargo, una dirección IP global puede utilizarse como un componente para un entorno de migración tras error, si desea evitar la propagación de DNS.
