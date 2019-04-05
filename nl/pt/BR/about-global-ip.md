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

# Sobre endereços IP globais
{:#about-global-ip-address}

Um endereço IP global é uma sub-rede secundária estática especializada. Ele é entregue como uma sub-rede
/32 (em outras palavras, um endereço IP único) que pode ser roteado para qualquer outro endereço IP na conta. Os endereços IPv4 e IPv6 estão disponíveis e cada tipo deve ser roteado para um endereço IP da mesma versão de IP. Os destinos de roteamento aceitáveis incluem os endereços IP primários em uso por seus servidores e quaisquer endereços IP de sub-rede secundário móveis. Os recursos exclusivos de um endereço IP global são estes:

  * Roteamento sob demanda para endereços IP em uma conta, globalmente.
  * O endereço é anunciado para a Internet por todos os roteadores de borda do {{site.data.keyword.cloud}}. Portanto, seus dados usam o caminho mais curto para a
rede {{site.data.keyword.cloud}} e, de lá, é possível utilizar o backbone global do {{site.data.keyword.cloud}} dedicado para atingir o destino que você configurou.

Os endereços IP globais fornecem flexibilidade. Eles permitem que você desloque cargas de trabalho entre servidores, mesmo entre data centers geograficamente distintos. Além disso, os endereços IP globais
fornecem persistência de IP, permitindo transições sem uma necessidade de adaptação (por exemplo, para
evitar caches DNS). O recurso de roteamento global é perfeito para a transição de cargas de trabalho em
sites de recuperação de desastre ou para transição perfeita para uma nova implementação em uma área
geográfica que pode servir melhor ao público.

| **Disponibilidade** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
| Rede pública   | Sim  | Sim  |
| Rede Privada  |      |      |


## Gerenciando endereços IP globais
{:#manage-global-ip-address}

Para gerenciar endereços IP globais, siga estas etapas:

 1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/){: new_window} e efetue login em sua conta.
 1. Na navegação do Portal do Cliente, selecione **Infraestrutura clássica**.
 1. No menu de navegação Infraestrutura clássica, selecione ** Rede > Gerenciamento de IP > IP global**.
 1. Você verá seus endereços IP globais listados. Utilize filtros para limitar sua procura, conforme necessário. 
 
Você pode observar que algumas entradas não têm um valor para **Destino**, o que indica que o endereço IP global não está roteado atualmente, portanto, não está em serviço.

### Roteando e cancelando roteamento de endereços
{:#route-unroute-address}

Depois de localizar o endereço IP global desejado, clique em seu identificador de sub-rede. Em
seguida, você verá uma tela que mostra seu destino de rota atual, se aplicável. Para rotear (enviar tráfego)
para um novo destino, você tem duas opções:

 * inserir um endereço IP completo ou
 * iniciar digitando um nome do host.
 
A digitação de um nome do host permite procurar o nome do host de um servidor, portanto, é possível consultar seu endereço IP. Depois de inserir um endereço IP, selecione **Atualizar**. Para cancelar o roteamento do endereço IP global, selecione **Limpar**. Quando o status
de entrada muda para informar 'Não roteado', selecione **Atualizar**.

O menu suspenso não é uma lista exaustiva dos endereços IP disponíveis. Insira manualmente o
endereço IP desejado se ele não estiver disponível na lista de seleção.
{:note}

### Com que frequência posso atualizar?
{:#how-often-can-i-update}

Somente uma única atualização de rota pode estar em andamento a qualquer momento. Se você tentar
atualizar a rota de um endereço IP global enquanto outra atualização estiver em andamento, receberá um
erro. Aguarde até que a atualização anterior seja concluída antes de tentar novamente.


## Como solicitar endereços IP globais
{:#how-to-order-global-ip-address}

Siga estas instruções para solicitar endereços IP globais:

  1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/){: new_window} e efetue login em sua conta.
  1. Na navegação do Portal do Cliente, selecione **Infraestrutura clássica**.
  1. No menu de navegação Infraestrutura clássica, selecione ** Rede > Gerenciamento de IP > IP global**.
  3. Clique no link **Novos endereços IP**.
  4. No menu suspenso, escolha **IPv4 global** ou **IPv6 global**, conforme necessário, e clique em **Continuar** para iniciar o processo de pedido.

![Figura 1](images/1_2.png)

### O que acontece a seguir?
{:#global-ip-address-next}

Ao bloquear todos os processos de aprovação necessários para o status de sua conta, uma nova sub-rede
de endereço IP global aparece em sua conta em alguns instantes.

### Limite de Recurso
{:#global-ip-resource-limit}

Uma conta pode ter apenas cinco (5) endereços IP globais por versão de IP. Por exemplo, cinco (5)
endereços IP globais IPv4 e cinco (5) endereços IP globais IPv6.

## Como cancelar endereços IP globais
{:#how-to-cancel-global-ip-address}

Se você não precisar mais de um endereço IP global, siga estas etapas para cancelá-lo:

  1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/){: new_window} e efetue login em sua conta.
  1. Na navegação do Portal do Cliente, selecione **Infraestrutura clássica**.
  1. No menu de navegação Infraestrutura clássica, selecione ** Rede > Gerenciamento de IP > IP global**.
  1. Conclua quaisquer filtros necessários para localizar o endereço desejado.
  1. No lado direito da entrada do endereço na lista de endereços, um círculo com um X é mostrado. Clique nesse ícone para iniciar o processo de cancelamento.
