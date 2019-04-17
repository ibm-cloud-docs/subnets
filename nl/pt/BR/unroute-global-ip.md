---
copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, unroute process, Device Global IP addresses

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# Remover o roteamento do endereço IP global de um dispositivo
{:#unroute-global-ip-address}

Os endereços IP globais podem ter o roteamento removido manualmente pelo usuário a qualquer momento. Siga as etapas abaixo para remover o roteamento de um endereço IP global de um dispositivo.

1. Navegue até a tela IP global no [Portal do Cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/). Consulte [Exibir
a tela IP global](/docs/infrastructure/subnets?topic=subnets-display-global-ip-screen){:new_window}.
* Selecione o endereço IP global a ter o roteamento removido.
* Selecione o botão **Limpar**.
* Selecione o botão **Atualizar** para concluir o processo de remoção de roteamento ou selecione **Cancelar** para cancelar a ação e retornar para a tela **Subnets**.

## O que acontece em seguida
{:#unroute-global-ip-next}

Depois que você remove o roteamento de um IP global de um dispositivo, o IP global não é mais associado a esse dispositivo. Após o processo de remoção de roteamento do IP global ser concluído, esse endereço IP global pode ser [roteado novamente](/docs/infrastructure/subnets?topic=subnets-route-global-ip-address-device) para qualquer outro dispositivo na conta.
