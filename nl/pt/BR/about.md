---
copyright:
  years: 1994, 2017
lastupdated: "2017-10-20"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Sobre sub-redes e IPs

O IBM Cloud fornece várias opções para pedir Sub-redes e endereços IP, assim é possível projetar uma infraestrutura que atenda às suas necessidades. Entender como as sub-redes funcionam e conhecer seus casos de uso desejados ajudarão a alcançar exatamente o que você precisa.

## Tipos de sub-redes

Conhecendo mais sobre cada tipo de sub-rede, é possível entender melhor como usá-las em sua infraestrutura em nuvem.

### Sub-redes primárias

As sub-redes primárias são designadas automaticamente pelo {{site.data.keyword.BluSoftlayer_notm}} em VLANs, para o propósito de fornecer uma provisão automatizada e serviços em suas VLANs. Essas sub-redes não estão disponíveis para os seus endereços IP ou serviços secundários, porque elas são usadas por nossos sistemas automatizados. As sub-redes primárias são designadas aos novos servidores automaticamente. Se tentar usá-las em seus servidores, você poderá causar um conflito de endereço IP e, nesse caso, será necessário remover o endereço IP. 

**Nota: não somos capazes de reservar endereços IP em Sub-redes primárias para seu uso.**

### Sub-redes móveis

As sub-redes móveis podem ser pedidas por meio do [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/) Essas sub-redes geralmente fornecem endereços de Máquina Virtual (VM) ou endereços IP secundários em servidores ou interfaces secundárias. Essas sub-redes também seriam usadas para endereços IP de cluster ou HA, porque elas são controladas por nossos roteadores por meio de ARP. Elas podem ser movidas facilmente. O formato padrão dessas sub-redes inclui seu próprio endereço de Rede, Gateway e Transmissão, portanto, três dos seus endereços IP estarão em uso imediatamente.

### Sub-redes estáticas

As sub-redes estáticas são outro tipo de sub-rede que pode ser pedido por meio do [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/network/subnets/order). As sub-redes estáticas geralmente são usadas para servidores da web, e-mail ou outros serviços hospedados em um servidor, que requerem vários endereços IP adicionais para permitir conexões. As sub-redes estáticas são exclusivas, porque deve-se especificar outro endereço IP existente que já esteja designado a um servidor para o qual a sub-rede é roteada diretamente. Você tem a flexibilidade de rotear a sub-rede conforme desejar e é possível movê-la para servidores diferentes – no entanto, para fazer isso, deve-se mudar o local roteado.

### Endereços IP globais

Para obter informações sobre a Oferta de IP global, consulte a [Documentação do IP global](about-global-ip.html).

## Considerações a serem levadas em conta com sub-redes diferentes

### Firewalls de hardware

As sub-redes móveis não são protegidas por firewalls por padrão. Se você precisar desse recurso, discuta isso com seu representante de vendas. As sub-redes que precisam ser protegidas não podem exceder uma sub-rede /29.

### Transferindo IPs móveis entre servidores

Ao transferir um IP móvel de um servidor para outro, certifique-se de que um pacote ARP gratuito seja enviado para que os nossos roteadores possam atualizar suas entradas ARP e encaminhar o endereço IP atualizado para o servidor correto. Se você não enviar o pacote ARP, poderá levar quatro horas ou mais para o endereço IP começar a responder corretamente.

### Gateways Vyatta

Ao pedir sub-redes para uma VLAN atrás de um Gateway Vyatta, assegure-se de que a sub-rede esteja incluída corretamente na configuração do Vyatta. Se estiver usando o VRRP para HA, assegure-se de que a sub-rede esteja configurada corretamente para permitir failover entre os dois dispositivos de gateway. Se você precisar de assistência adicional com essas tarefas, consulte estes dois artigos sobre como configurar o Gateway Vyatta:

 * [Dispositivos de gateway de rede Vyatta](../network-gateways/network-gateway-devices-vyatta.html)

 * [Configuração de alta disponibilidade do Vyatta](../vyatta/vyatta-high-availability-configuration.html)
 
 ### Cancelando sub-redes
 
As sub-redes que são designadas automaticamente a uma conta para o cumprimento de ordens de dispositivo estão sujeitas a solicitações automáticas quando essas sub-redes não são mais referenciadas. As sub-redes que são pedidas separadamente podem ser canceladas a qualquer momento.
