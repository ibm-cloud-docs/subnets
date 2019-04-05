---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Uso de subredes secundarias en máquinas virtuales autoalojadas
{:#use-secondary-subnets-self-hosted-vms}

Al alojar sus propias máquinas virtuales si desea que esas máquinas virtuales sean ciudadanos de primera clase en la red de {{site.data.keyword.BluSoftlayer_notm}}, es necesario utilizar **Subredes secundarias**. Discutiremos una forma flexible de proporcionar las direcciones IP de las VM utilizando uno o más hosts de máquina virtual, tanto si participan en las configuraciones de clúster como si no.

A lo largo de este caso de ejemplo, consulte [Acerca de las subredes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) para obtener más detalles sobre los tipos de subredes descritos.

Imaginemos que tiene dos servidores nativos, llamémosles `aunt` y `uncle`. Ambos serán hosts de las máquinas virtuales, y cada uno de ellos ya tiene sus direcciones IP asignadas desde una **Subred primaria**. Necesita direcciones IP adicionales para las máquinas virtuales. Puede utilizar cualquier tipo de subred secundaria para conseguir esto, pero se recomienda utilizar una **Subred secundaria portátil** como origen de las direcciones utilizadas por las máquinas virtuales. Una subred portátil proporciona acceso tanto de `aunt` como de `uncle` a las direcciones IP definidas por la subred. De esta forma, puede compartir esas direcciones IP en ambos servidores, y si utiliza técnicas de migración para las máquinas virtuales, puede transferir máquinas virtuales a través de dichos servidores sin interrupciones.

Ahora imaginemos que ha creado dos máquinas virtuales, `VPS1` y `VPS2`, ha adquirido la subred portátil 129.42.0.0/29, y ha asignado dos direcciones desde la misma hasta las máquinas virtuales. La utilización de direcciones IP sería algo parecido a lo siguiente:

129.42.0.0/29 - Subred secundaria portátil
```
129.42.0.0 – Red
129.42.0.1 – Pasarela
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Difusión
```

Ahora imaginemos que desea que VPS1 tenga más direcciones IP para segregar los servicios que proporciona. Puede asignar más direcciones de la subred 129.42.0.0/29, pero es posible que sólo desee utilizar dicha subred para poner las VM en línea, no para sus servicios. Tiene dos opciones: 1) adquirir otra subred portátil 2) adquirir una subred estática. Si recuerda de la descripción de las subredes portátiles versus las estáticas en [Acerca de las subredes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), sabrá que si bien las subredes portátiles proporcionan flexibilidad, no le dan acceso a todas las direcciones IP. Si solo necesita unas cuatro direcciones IP adicionales, adquirir una subred estática es una opción eficiente. Vamos a probar esta opción.

Adquiere una subred estática y recibe 129.42.0.100/30. Durante la compra, la direcciona a 129.42.0.3 o a VPS1 en este caso de ejemplo. Hacerlo así le permite usar las cuatro direcciones IP en cualquier servidor que esté respondiendo a 129.42.0.3, de nuevo, eso es actualmente VPS1, pero podría transferir 129.42.0.3 a VPS2 en cualquier momento y esas cuatro nuevas direcciones IP de 129.42.0.100/30 seguirían. Por lo tanto, volvamos a echar un vistazo a la utilización de las direcciones IP:

129.42.0.0/29 - Subred secundaria portátil
```
129.42.0.0 – Red
129.42.0.1 – Pasarela
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Difusión
```

129.42.0.100/30 - Subred secundaria estática
```
129.42.0.100 – 129.42.0.3 (también denominada VPS1)
129.42.0.101 – 129.42.0.3 (también denominada VPS1)
129.42.0.102 – 129.42.0.3 (también denominada VPS1)
129.42.0.103 – 129.42.0.3 (también denominada VPS1)
```

Para recapitular, hemos utilizado una subred portátil para hacer que las direcciones IP estén disponibles para todos los hosts de máquinas virtuales y, a continuación, hemos hecho que haya direcciones IP adicionales disponibles para una máquina virtual utilizando una subred estática. Podría haber utilizado direcciones fuera de la subred portátil original, o simplemente añadir otra subred portátil. Esperamos que este ejemplo ilustre no sólo que es correcto dirigir las subredes estáticas a direcciones IP en subredes portátiles, sino que hacerlo es realmente eficiente y útil.
