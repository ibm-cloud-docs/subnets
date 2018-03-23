---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Gerenciar endereços IP globais

É possível gerenciar seus endereços IP globais na tela **Sub-redes**. 

1. Em seu navegador, abra o [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/){: new_window} e efetue login em sua conta.
2. Na navegação do Portal do cliente, selecione **Rede > Gerenciamento de IP > Sub-redes**.
3. No menu suspenso, escolha **IPv4 global** (ou IPv6) para filtrar a lista de Sub-redes para mostrar somente os IPs globais.
4. Clique no IP global que você deseja gerenciar.
 
  **Nota: um IP global é um endereço IP estático que pode ser roteado para qualquer servidor dentro da rede IBM Cloud. A oferta de endereço
IP estático atual pode ser roteada somente para um endereço IP dentro do mesmo data center, mas os endereços IP globais não compartilham
essa restrição.**

5. Na página Gerenciamento de endereço IP, insira o endereço IP do servidor para o qual você deseja rotear o endereço IP global e insira quaisquer notas aplicáveis, em seguida, selecione **Atualizar**.

![Figura 2](images/2_1.png)

## Incluir um IP global em seu servidor 

Antes que seu servidor aceite o tráfego para o IP global, esse IP deve ser incluído no sistema de forma adequada. Cada sistema requer comandos um pouco diferentes, então eles são mostrados nas próximas seções.

### Para servidores Linux:

**Red Hat/CentOS**

1. Edite (vim ou nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* Inclua as linhas a seguir:
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. Edite `/etc/network/interfaces`

* Inclua as linhas a seguir:

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

Se o seu sistema não funciona de forma adequada, inclua as linhas a seguir no lugar, substituindo o # pelo próximo número disponível:

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### Para servidores Windows

1. Navegue para: **Iniciar -> Painel de Controle -> Conexões de rede -> Conexão de área local (pública) (propriedades)**.
* Selecione: **Protocolo da Internet (TCP/IP)** e clique em **Propriedades -> Avançado**.
* Selecione **Incluir** na seção de endereços IP e insira o Endereço IP e a Máscara de sub-rede.
* Quando essa tarefa for concluída, simplesmente clique em "OK" para voltar para a área de trabalho.

Para verificar se suas definições entraram em vigor, abra um prompt do DOS navegando para **Iniciar -> Executar -> "cmd"** e execute o comando

```
        > ipconfig /all
```

**Notas:**

* Se você já tiver um arquivo `eth1:1` em seu servidor como no exemplo acima, incremente o último dígito para o próximo número inteiro disponível.
* A modificação de um endereço IP global para um novo servidor ou VSI requer até cinco minutos para entrar em vigor. 
* Dentro da rede IBM Cloud, a mudança de rota leva menos de 1 minuto para atualizar.
* Os IPs globais não funcionam para balanceadores de carga local.
* Os IPs globais são distribuídos por meio da uma sub-rede exclusiva; os IPs de cliente existentes não podem ser convertidos nem usados como IPs globais.
* Por si próprios, os IPs globais não são uma solução de failover automático, porque eles não têm verificações de funcionamento; no entanto, um endereço IP global pode ser usado como um componente para um ambiente de failover, se você deseja contornar a propagação de DNS.
