---
copyright:
  years: 1994, 2017, 2018, 2019
lastupdated: "2018-02-28"

keywords: Ms IP addresses, Use Secondary Subnets, own virtual machines

subcollection: subnets

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Usar sub-redes secundárias em VMs auto-hospedadas
{:#use-secondary-subnets-self-hosted-vms}

Ao hospedar suas próprias máquinas virtuais e desejar que essas máquinas virtuais sejam cidadãos
de primeira classe na rede do {{site.data.keyword.BluSoftlayer_notm}}, é necessário utilizar **Sub-redes secundárias**. Vamos discutir uma maneira flexível para fornecer endereços
IP de suas VMs usando um ou mais hosts de máquina virtual, participando de configurações em cluster ou não.

Ao longo do curso deste cenário, consulte [Sobre sub-redes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) para
obter mais detalhes sobre os tipos de sub-redes descritos.

Então, suponhamos que você tenha dois servidores bare metal, vamos chamá-los de
`aunt` e `uncle`. Os dois serão host para suas próprias máquinas virtuais
e cada um já tem seus próprios endereços IP designados de uma **Sub-rede primária**. Você precisa de endereços IP adicionais para suas máquinas virtuais. Você poderia usar qualquer tipo de sub-rede secundária para conseguir isso, mas recomendamos o uso de uma **Sub-rede secundária móvel**
como a origem de endereços usados por suas VMs. Uma sub-rede móvel fornece acesso a `aunt` e `uncle` para os endereços IP definidos pela sub-rede. Dessa forma, é possível compartilhar
esses endereços IP entre os dois servidores e se você utilizar técnicas de migração para suas VMs, poderá
transferir as VMs entre esses servidores sem problemas.

Agora, suponhamos que você tenha criado duas máquinas virtuais, `VPS1` e `VPS2`, comprado a sub-rede móvel 129.42.0.0/29 e designado dois endereços dele
para suas máquinas virtuais. A utilização do endereço IP seria algo semelhante a isso:

129.42.0.0/29 - Sub-rede secundária móvel
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

Agora, suponhamos que você deseje que o VPS1 tenha mais endereços IP para segregar os serviços que ele está fornecendo. É possível designar absolutamente mais endereços fora da sub-rede 129.42.0.0/29, mas você pode desejar usar somente essa sub-rede para colocar VMs on-line, não para seus serviços. Você
tem duas opções: 1) comprar outra sub-rede móvel 2) comprar uma sub-rede estática. Se você fizer a
rechamada das descrições de sub-redes móveis versus estáticas em [Sobre sub-redes](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips),
saberá que, embora as sub-redes móveis forneçam flexibilidade, elas também não dão acesso a todos os
endereços IP. Se você precisava somente de quatro endereços IP adicionais, comprar uma sub-rede estática
é uma opção eficiente. Vamos tentar isso.

Você compra uma sub-rede estática e recebe 129.42.0.100/30. Durante a compra, roteie-o para
129.42.0.3 ou VPS1 neste cenário. Fazer isso fornece a você todos os quatro endereços IP para usar em
qualquer servidor que esteja respondendo a 129.42.0.3, novamente, que atualmente é o VPS1, mas você
poderia transferir o 129.42.0.3 para o VPS2 a qualquer momento e os quatro novos endereços IP do
129.42.0.100/30 seguiriam! Então, vamos verificar a utilização do endereço IP novamente:

129.42.0.0/29 - Sub-rede secundária móvel
```
129.42.0.0 – Network
129.42.0.1 – Gateway
129.42.0.2 –
129.42.0.3 – VPS1
129.42.0.4 –
129.42.0.5 – VPS2
129.42.0.6 –
129.42.0.7 – Broadcast
```

129.42.0.100/30 - Sub-rede secundária estática
```
129.42.0.100 – 129.42.0.3 (aka VPS1)
129.42.0.101 – 129.42.0.3 (aka VPS1)
129.42.0.102 – 129.42.0.3 (aka VPS1)
129.42.0.103 – 129.42.0.3 (aka VPS1)
```

Para recapitular, usamos uma sub-rede móvel para disponibilizar endereços IP a todos os hosts de máquina virtual e, em seguida, disponibilizamos endereços IP adicionais para uma máquina virtual usando
uma sub-rede estática. Você poderia definitivamente ter usado endereços fora da sub-rede móvel original
ou simplesmente incluído outra sub-rede móvel. Esperamos que esse cenário ilustre que não só é correto rotear sub-redes estáticas para endereços IP em sub-redes móveis, como também é realmente eficiente e
útil fazê-lo.
