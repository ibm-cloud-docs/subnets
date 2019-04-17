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

# Sobre Subnets e IPs
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} tem terminologia específica para os tipos e usos de sub-redes encontradas em nossa plataforma. Conhecer o
uso pretendido o ajudará a saber a melhor maneira de usá-los em sua infraestrutura em nuvem.


## Tipos de Subnets
{:#subnet-types}

### Subnets primárias
{:#primary-subnets}

As sub-redes primárias são designadas automaticamente pelo {{site.data.keyword.BluSoftlayer_notm}} e são o que fornece endereços IP para recursos, conforme necessário. Designamos e removemos as sub-redes primárias conforme necessário para o cumprimento de outros produtos. Todos os servidores serão provisionados
com pelo menos um endereço IP de uma sub-rede primária, comumente referida como um endereço IP primário. Alguns produtos e opções resultam em endereços IP mais primários que estão sendo designados.

É importante entender que os endereços IP em sub-redes primárias, que ainda não estão designados a
recursos, não estão disponíveis para o seu uso. Se você tentar usar endereços IP não designados de sub-redes primárias, as designaremos inevitavelmente a outro recurso em algum ponto. Isso leva a conflitos de IP na rede e à interrupção no serviço geral. Reservamo-nos o
direito de bloquear ou, de qualquer outra forma, tornar inutilizável qualquer endereço IP em uma sub-rede
primária que não seja especificamente designada durante o cumprimento de outros produtos. 

**Recomendamos fortemente** usar **Sub-redes secundárias** como seus endereços IP de aplicativos/serviços externos; especialmente ao projetar aplicativos multisservidor. Usar os endereços IP primários designados a seus servidores é perfeitamente normal. No entanto, isso não
tem a flexibilidade de manter endereços conhecidos para seus serviços, que são agnósticos de cancelamento
e pedidos de servidor. Não há garantias feitas com relação à ordem em que os endereços IP primários são designados, tal como crescente, decrescente, ignorando diferenças, etc.

Sob nenhuma circunstância, podemos reservar endereços IP em sub-redes primárias para seu uso.
{:note}

### Sub-redes secundárias
{:#secondary-subnets}

As sub-redes secundárias fornecem endereços IP adicionais para muitas necessidades. Diferentemente das sub-redes primárias, essas sub-redes são de sua propriedade para a duração do seu uso e não serão removidas,
a menos que você as cancele. As sub-redes secundárias devem ser usadas quando você precisar de um endereço IP estável que não deve ser dependente de nenhum dispositivo de cálculo específico. Os usos de exemplo incluem:

  * Endereços IP que você pode designar a suas próprias máquinas virtuais, locais e virtuais.
  * Vários endereços IP de serviço distintos hospedados por um único servidor, permitindo que você identifique facilmente o tráfego. Comumente usados com servidores da web e TLS.
  * Um endereço IP de serviço vinculado ao DNS. Evite atrasos de armazenamento em cache de DNS
ao deslocar cargas de trabalho para novos servidores (ou seja, o IP de serviço não será mudado simplesmente porque o endereço IP principal de um servidor muda!)
.
  * Configurações de alta disponibilidade que utilizam protocolos de endereço IP "flutuantes".

Para alcançar tais usos, e muito mais, oferecemos opções de roteamento diferentes para sub-redes secundárias. Para ajudar a ilustrar as diferenças entre as sub-redes secundárias que oferecemos, vamos
nos referir à sub-rede de exemplo abaixo em explicações adicionais.

Aqui está um exemplo dos endereços IP fornecidos pela sub-rede 10.0.0.0/29:
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

#### Subnets estáticas
{:#static-subnets}

Uma sub-rede estática fornece um destino único com acesso a todos os endereços IP definidos por essa sub-rede. Um benefício do uso de uma sub-rede estática é que o dispositivo de destino é capaz de utilizar
todos os endereços IP definidos; não está sofrendo a penalidade de uso de rede, gateway e endereço de
transmissão usual. Portanto, usando nossa sub-rede de exemplo, todos os endereços são utilizáveis:

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

Dessa forma, se um servidor tiver o endereço IP 10.0.0.13 e você rotear 10.0.0.0/30 estaticamente para 10.0.0.13, esse servidor agora poderá ligar quatro endereços IP adicionais; recebendo o tráfego em cada um individualmente. É importante entender que não há nenhuma Conversão de Endereço de Rede (NAT) sendo executada para qualquer um dos endereços fornecidos. Cada endereço pode ser usado nativamente em
servidores e, portanto, cada um pode ser usado para propósitos distintos.

| **Disponibilidade** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rede pública   | Sim  | Sim  |
| Rede Privada  |      |      |

#### Subrede Móvel
{:#portable-subnet}

Uma sub-rede móvel fornece seus endereços IP para todos os recursos em uma VLAN. Isso significa
que qualquer recurso de cálculo na mesma VLAN pode utilizar qualquer endereço fornecido pela sub-rede. Esse comportamento é muito útil para endereços "flutuantes" em múltiplos recursos e desacopla a sub-rede de
qualquer recurso específico. Uma necessidade de sub-redes móveis é que nem todos os endereços IP definidos pela sub-rede são utilizáveis pelos dispositivos. Mecanismos de rede requerem alguns dos
endereços IP a serem consumidos. Esses endereços consumidos são referidos como os endereços IP de
transmissão, de rede e de gateway. Observe os endereços que estão disponíveis em nosso exemplo:

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

| **Disponibilidade** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rede pública   | Sim  | Sim  |
| Rede Privada  | Sim  |      |


### Endereços IP globais
{:#global-ip-addresses}

Para obter informações sobre a oferta de IP global, consulte a [Documentação do IP global](/docs/infrastructure/subnets?topic=subnets-about-global-ip-address).

| **Disponibilidade** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rede pública   | Sim  | Sim  |
| Rede Privada  |      |      |


## Cancelando Subnets
{:#canceling-subnets}

Se você não precisar mais de uma sub-rede secundária, siga estas etapas para cancelá-la:

  1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/){: new_window} e efetue login em sua conta.
  1. Na navegação do Portal do Cliente, selecione **Infraestrutura clássica**. 
  1. No menu de navegação Infraestrutura clássica, selecione ** Rede > Gerenciamento de IP > Sub-redes**.
  1. Escolha quaisquer filtros desejados para localizar a sub-rede desejada.
  1. No lado direito da entrada da sub-rede na lista de sub-redes, um círculo vermelho com um X será mostrado. Clique nesse ícone para iniciar o processo de cancelamento.


## Considerações específicas do produto ao solicitar sub-redes
{:#product-specific-considerations-subnets}

### Hardware Firewall (Shared)
{:#hardware-firewall-subnets}

As Subnets móveis não são protegidas por firewalls por padrão. Se você precisar desse recurso, discuta isso com seu representante de vendas. As sub-redes secundárias maiores que /29 não podem ser roteadas por
meio dessa oferta de firewall.

### Transferindo endereços IP de sub-rede móvel entre servidores
{:#transferring-portable-subnet-ip-between-servers}

Ao transferir um endereço IP de um servidor para outro, certifique-se de que um pacote ARP gratuito
seja enviado. Isso permite que nossos roteadores atualizem sua entrada ARP e encaminhem o tráfego para
o servidor correto. Não fazer isso pode resultar em um atraso de até quatro horas no novo servidor que recebe
o tráfego para o endereço transferido.

### Dispositivos de roteador virtual
{:#virtual-router-appliances-subnets}

Ao solicitar sub-redes para uma VLAN atrás de um dispositivo de roteador virtual de alta disponibilidade, assegure-se de que a sub-rede esteja configurada corretamente para permitir failover
entre os dois dispositivos. A assistência detalhada está descrita na documentação [Configuração de alta disponibilidade do VRA](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp).
