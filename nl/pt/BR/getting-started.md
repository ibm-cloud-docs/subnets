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

# Introdução a Subnets e IPs
{:#getting-started-subnets-ips}

As sub-redes são uma parte importante de como você usa a Internet e isso também é verdade ao
usar o {{site.data.keyword.cloud}}. Temos terminologia específica para os tipos e usos de sub-redes encontradas em nossa plataforma. Cada sub-rede fornece endereços IP aos recursos de diferentes maneiras. Você encontrará os tipos de sub-redes a seguir e ao saber mais sobre cada tipo de sub-rede, é possível entender
como melhor usá-los em sua infraestrutura de nuvem.

  * Sub-redes primárias - sub-redes designadas para atender às necessidades de endereçamento IP
de outros produtos, tais como servidor bare metal e instâncias do servidor virtual. Essas sub-redes são automaticamente designadas e removidas.
  * Sub-redes secundárias - sub-redes que são compradas e roteadas por você; canceladas quando
não são mais necessárias. Há dois subtipos:
    * Móvel - endereços IP estão disponíveis para todos os recursos em uma VLAN.
    * Estático - endereços IP estão disponíveis para o recurso identificado como o terminal de roteamento.
  * Endereços IP globais - comportamento de roteamento exclusivo que utiliza o backbone do {{site.data.keyword.cloud}} que fornece endereços IP para o recurso identificado como o terminal
de roteamento.

Revise cada tipo em detalhes em [Sobre sub-redes e IPs](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) para revisar aspectos como IPv4 versus IPv6 e disponibilidade de rede pública/privada.

Para entender sub-redes e a criação delas de maneira mais geral, revise [Sub-rede ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://en.wikipedia.org/wiki/Subnetwork).
Além disso, você verá que nos referimos a sub-redes usando [Notação CIDR ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


## Solicitando sub-redes
{:#ordering-subnets}

Siga estas etapas para solicitar sub-redes que fornecem endereços IP adicionais:

  1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/){: new_window} e efetue login em sua conta.
  1. Na navegação do Portal do Cliente, selecione **Infraestrutura clássica**. 
  1. Na navegação Infraestrutura clássica, selecione ** Rede > Gerenciamento de IP > Sub-redes**.
  1. Selecione o link, "Novos endereços IP", na parte superior direita da listagem.
  1. Para iniciar o processo de solicitação, selecione o tipo Público ou Privado de sub-rede nos botões de opções.
  1. Escolha entre as opções IPv4 ou IPv6.
  1. Para escolher IPs estáticos ou globais, clique na caixa correspondente. 
    1. Para IPv4, use a lista suspensa disponível nas opções Estático ou Móvel para escolher quantos endereços você deseja. 
  1. Selecione a VLAN para estabelecer onde os novos endereços IP são roteados.
  1. Preencha as informações restantes solicitadas e clique em **Criar**.


Após uma sub-rede ter sido comprada, o tipo e o destino de roteamento não podem ser mudados. Deve-se solicitar uma nova sub-rede para adquirir um tipo ou terminal de roteamento diferente.

### O que acontece a seguir?
{:#ordering-subnets-next}

Ao bloquear todos os processos de aprovação necessários para o status de sua conta, uma nova
sub-rede com sua configuração desejada aparecerá em sua conta em alguns instantes.
