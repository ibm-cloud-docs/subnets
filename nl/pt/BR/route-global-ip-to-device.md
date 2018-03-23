---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-05"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Rotear um endereço IP global para um dispositivo

Os endereços IP globais são roteados manualmente pelo usuário para qualquer dispositivo que o {{site.data.keyword.BluSoftlayer_notm}} oferece. Para rotear um IP global para um dispositivo, o dispositivo deve ser associado à conta que possui o IP global. Siga as etapas abaixo para rotear um endereço IP global para um dispositivo.

1. Navegue até a tela IP global no [Portal do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com/). Consulte [Exibir a tela IP global](display-global-ip-screen.html){:new_window}.
* Selecione a sub-rede de IP global a ser roteada.
* Inicie digitando o endereço IP do dispositivo para o qual o IP global roteará no campo **Rotas para**. Esse campo será concluído automaticamente com base em sua entrada. Ele exibe qualquer dispositivo associado à sua conta.
* Insira quaisquer notas pertinentes sobre o IP global, dispositivo ou outros itens no campo **Notas**.
* Selecione o botão **Atualizar** para concluir a rota ou selecione **Cancelar** para cancelar a ação e retornar para a tela **Sub-redes**.

## O que acontece em seguida

Quando você inicia a rota de sub-rede de IP global, o processo é iniciado. As rotas geralmente levam menos de um minuto para serem concluídas. A qualquer momento, é possível [remover o roteamento](unroute-global-ip.html) de IP global do dispositivo.
