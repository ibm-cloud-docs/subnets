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

# Perguntas Mais Frequentes
{:#subnets-faq}

## O que significa `IP primário somente para o futuro servidor` quando eu verifico
os endereços IP de uma sub-rede?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

As sub-redes primárias são designadas e removidas, conforme necessário, pelo {{site.data.keyword.BluSoftlayer_notm}} para outros recursos que você solicitou, tais como
servidores bare metal ou instâncias de servidor virtual. Nós não simplesmente designamos um endereço IP a cada vez, nós designamos uma sub-rede. Isso significa que, às vezes, há espaço adicional para recursos
futuros. Essa designação está afirmando que esses endereços serão usados por recursos futuros. Veja a
pergunta, "**Posso usar os outros endereços IP definidos pelas sub-redes primárias que
vejo?**" para obter o motivo para não considerar esses endereços IP como utilizáveis.


## Posso usar os outros endereços IP definidos pelas sub-redes primárias que vejo?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

Não! Percebemos que você vê as sub-redes primárias designadas por {{site.data.keyword.BluSoftlayer_notm}} como qualquer outra sub-rede, mas como descrito em [Sobre sub-redes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips), as sub-redes primárias são o que fornece endereços IP aos recursos sob demanda. Nós designamos e removemos
sub-redes primárias conforme necessário para o cumprimento de outros produtos. Se você tentar usar
endereços IP não designados de sub-redes primárias, inevitavelmente os designaremos a outro recurso em algum momento. Isso leva a conflitos de IP na rede e à interrupção no serviço geral. Reservamo-nos o
direito de bloquear ou, de qualquer outra forma, tornar inutilizável qualquer endereço IP em uma sub-rede
primária que não seja especificamente designada durante o cumprimento de outros produtos. É necessário
usar **Sub-redes secundárias** para todas as necessidades de endereço IP adicionais
e o encorajamos fortemente a usá-las para suas necessidades de endereço de aplicativo/serviço. As
sub-redes secundárias são muito mais flexíveis e são mantidas na sua conta enquanto você as possuir.


## Existe uma maneira de especificar qual sub-rede eu desejo usar para o meu dispositivo quando
eu solicitá-la?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

Sim, uma sub-rede específica pode ser especificada durante o processo de solicitação. Ao pedir um dispositivo, essa opção estará disponível no final do formulário de pedido. Após a seleção de uma VLAN privada, uma lista de sub-redes primárias roteadas para essa VLAN é apresentada. É possível selecionar uma sub-rede desejada. O mesmo processo pode ser repetido para a VLAN pública e a sub-rede.

É importante observar que o envio da solicitação **não garante** que um endereço IP esteja disponível na sub-rede solicitada. Se nenhum endereço estiver disponível, você será
contatado para determinar um curso de ação. Para obter a melhor experiência com o {{site.data.keyword.BluSoftlayer_notm}}, a seleção de uma sub-rede é desencorajada para usos típicos.


## Eu fiquei sem endereços IP e agora?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

Isso não vai acontecer! Designamos automaticamente as sub-redes primárias para disponibilizar mais
endereços IP para cumprir suas compras de cálculo. Você não precisa administrar nada. No entanto, se
você quer dizer que precisa de mais endereços IP para, digamos, máquinas virtuais locais ou aplicativos
de segregação, leia sobre **Sub-redes secundárias** em [Sobre sub-redes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips).


## Como designo mais endereços IP a um recurso de cálculo?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

Primeiro, você desejará comprar uma **Sub-rede secundária**, há diversos
tipos, portanto, revise [Sobre
sub-redes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips). Depois de ter uma sub-rede roteada para o endereço IP ou VLAN desejada, você desejará
se referir à documentação de cálculo específica para saber como configurar seus novos endereços IP:

  * [Designação
de endereço IP do servidor bare metal](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Designação de
endereço IP da instância de servidor virtual](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## O que significa `Reservado para HSRP` quando eu verifico endereços IP de uma sub-rede?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

Em um número decrescente de locais, o {{site.data.keyword.BluSoftlayer_notm}} possui
roteadores que utilizam uma técnica conhecida como Hot Router Standby Protocol ou HSRP. Especificamente,
a maneira como isso é usado afeta os endereços IP disponíveis para ***Sub-redes secundária móveis***; significando que você perderá o acesso a dois endereços adicionais nesses locais. Como a designação "Reservado para HSRP" indica, esses endereços IP são reservados para atender
às necessidades do HSRP. Você pode até ter sub-redes no mesmo roteador, algumas com e algumas sem tais
reservas. Como com qualquer conflito de IP, não tente usar estes endereços ou você corre o risco de
afetar o tráfego em toda a sub-rede.

