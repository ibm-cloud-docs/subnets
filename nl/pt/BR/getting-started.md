---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Introdução a sub-redes e IPs

Os clientes do IBM Cloud podem pedir sub-redes estáticas, sub-redes móveis públicas e privadas ou sub-redes globais que consistem em endereços IPv4 e IPv6 a qualquer momento. 

Para pedir sub-redes e IPs:

1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/){: new_window} e efetue login em sua conta.
2. Na navegação do Portal do cliente, selecione **Rede > Gerenciamento de IP > Sub-redes**.
3. Para iniciar o processo de pedido, selecione o tipo apropriado de sub-rede no menu suspenso. 

**Observe que as sub-redes são criadas para clientes em uma base de caso a caso, que envolve um processo de análise minuciosa que examina uma razão de IP para servidor.**

## Entendendo os blocos de IP estático e móvel
O {{site.data.keyword.BluSoftlayer_notm}} oferece atualmente dois tipos diferentes de blocos de IP: estático ou móvel. Eles são projetados para serem usados de diferentes maneiras. Segue uma breve descrição de cada tipo de bloco, também incluindo uma seção sobre o uso desses endereços IP dentro de uma Máquina Virtual.  
### Bloco de IP Estático
O tipo mais comumente usados de bloco de IP na rede {{site.data.keyword.BluSoftlayer_notm}} é o bloco de IP estático. Um bloco de IP estático é roteado diretamente para um IP específico em nossa rede. Cada endereço IP em um bloco estático é utilizável no servidor. Um benefício primário de usar um bloco de IP estático é que você não perde os dois primeiros e últimos endereços IP – todos os endereços no bloco são utilizáveis. 

Aqui está um exemplo de um bloco de IP estático pequeno (192.168.0.4/30), mostrando que todos os quatro IPs nesse bloco estariam disponíveis para o servidor:
```
·192.168.0.4 – Endereço utilizável
·192.168.0.5 – Endereço utilizável
·192.168.0.6 – Endereço utilizável
·192.168.0.7 – Endereço utilizável
```
Com um bloco móvel, somente um único IP desse bloco seria realmente utilizável no servidor, porque os endereços IP de rede, gateway e transmissão estão ligados diretamente à VLAN.  

Nota: uma técnica especial permite que você use todos os IPs, porque usar a máscara de sub-rede designada só permitirá que você use todos, exceto um (o IP de transmissão). Para usar todos os IPs, use a máscara de sub-rede de 255.255.255.255, em vez de perder o IP de transmissão.

### Bloco de IP móvel
Um bloco de IP móvel pode ser usado em múltiplos servidores dentro de uma única VLAN simultaneamente. Oferecemos dois tipos diferentes de blocos de IP móveis:

 * O primeiro tipo de bloco de IP móvel é um bloco “Roteado para a VLAN”. Esse é um bloco de IP estático que é roteado para uma VLAN inteira em vez de um endereço IP específico.
 * O outro tipo de Bloco de IP móvel é um bloco “Secundário na VLAN”, que é projetado para ser usado em um Ambiente Virtual.
 
A diferença primária entre os dois é o número de IPs que estão disponíveis para uso. 

Um **bloco Roteado para a VLAN**, como um bloco estático, fornece acesso a todos os IPs dentro do bloco. No entanto, um bloco **Secundário na VLAN** requer que os IPs de Rede, Gateway e Transmissão estejam ligados diretamente à VLAN, que os torna inutilizáveis. Um bloco **Roteado para a VLAN** seria usado quando o usuário desejasse usar qualquer IP dentro desse bloco em qualquer servidor dentro da VLAN a qualquer momento. O bloco **Secundário na VLAN** é usado em conjunto com uma Máquina Virtual. Mais informações sobre blocos **Secundários na VLAN** são fornecidas sob a seção _IPs para máquinas virtuais_.

Ao pedir um bloco de IP móvel, por padrão, o {{site.data.keyword.BluSoftlayer_notm}} fornecerá um bloco **Secundário na VLAN**. Se você desejar que esse bloco seja convertido em um bloco **Roteado para a VLAN** para uso em seus servidores dentro de uma única VLAN, abra um chamado de suporte solicitando que esse bloco seja convertido em um bloco **Roteado para a VLAN**

### PODs que suportam Hot Standby Router Protocol (HSRP)

É importante notar que os PODs que aproveitam o Hot Standby Router Protocol (HSRP) utilizam dois endereços IPv4 adicionais: um para a interface VLAN de cada roteador participante, de cada bloco **Secundário na VLAN** configurado na VLAN. A maioria dos nossos PODs suporta HSRP.

O que segue é um exemplo de um bloco **Secundário na VLAN** (192.168.0.4/28) sendo usado para múltiplas Máquinas Virtuais múltiplos em um POD HRSP.
```
192.168.0.0 –  Endereço de rede
192.168.0.1 –  Endereço do gateway
192.168.0.2 –  Interface VLAN do roteador A
192.168.0.3 –  Interface VLAN do roteador B
192.168.0.4 –  VPS1
192.168.0.5 –  VPS2
192.168.0.6 –  VPS3
192.168.0.8 –  VPS4
192.168.0.9 –  VPS5
192.168.0.10 – VPS6
192.168.0.11 – VPS7
192.168.0.12 – VPS8
192.168.0.13 – VPS9
192.168.0.14 – VPS10
192.168.0.15 – Endereço de transmissão
```
 
### IPs para Máquinas Virtuais
As Máquinas Virtuais (VMs) são normalmente usadas em cargas de trabalho em nuvem, às vezes chamadas de "instâncias" ou "cálculos". Esta seção fornece informações sobre quais tipos de blocos de IP são necessários para uso em uma VM. As informações fornecidas aqui são baseadas no Microsoft Hyper-V.

Cada VM conectada à rede {{site.data.keyword.BluSoftlayer_notm}} em um ambiente virtual requer um endereço IP primário de um bloco móvel de IPs, porque o Hyper-V requer que cada VM forneça um endereço de Rede, Gateway e Transmissão na mesma sub-rede que o IP primário designado a essa VM. Uma vantagem de nossa rede de configuração é que um único bloco **Secundário na VLAN** pode ser usado para múltiplas Máquinas Virtuais. 

O que segue é um exemplo de um bloco **Secundário na VLAN** (192.168.0.4/29) sendo usado para múltiplas Máquinas Virtuais:
```
·192.168.0.0 – Endereço de rede
·192.168.0.1 – Endereço do gateway
·192.168.0.2 – VPS1
·192.168.0.3 – VPS1
·192.168.0.4 – VPS1
·192.168.0.5 – VPS2
·192.168.0.6 – VPS3
·192.168.0.7 – Endereço de transmissão
```
Conforme mostra o exemplo, esse bloco **Secundário na VLAN** fornece 5 endereços IP utilizáveis dos 8 endereços IP no bloco, ligados em 3 Máquinas Virtuais diferentes. Essa configuração traz a pergunta: “Como incluir mais IPs em um Máquina Virtual se todos os IPs no bloco Móvel são usados?”. Esse problema pode ser resolvido por meio do uso de um bloco estático ou um bloco móvel **Roteado para a VLAN**.

Para usar um bloco estático dentro de uma VM, primeiro peça um novo bloco de IP estático no Portal do cliente. Conforme você pede esse bloco, é possível selecionar o endereço IP para o qual deseja que esse bloco seja roteado. Selecionando o endereço IP que está designado à VM, o novo bloco será roteado especificamente para essa VM. Em seguida, é possível ligar o novo bloco de IPs diretamente a essa VM e começar a usá-los imediatamente.

Como alternativa, se você deseja que o novo bloco seja utilizável por mais de uma Máquina Virtual, use um bloco **Roteado para a VLAN**. Um bloco **Roteado para a VLAN** está disponível comprando um bloco de IP móvel do portal e selecionando a VLAN dentro da qual o endereço IP da VM reside. Após o bloco de IP ser criado, ele fica disponível para uso em qualquer servidor ou VM nessa VLAN.
