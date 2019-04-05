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

# 常見問題
{:#subnets-faq}

## 我在查看子網路的 IP 位址時，`僅適用於未來伺服器的主要 IP` 是什麼意思？
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

主要子網路會由 {{site.data.keyword.BluSoftlayer_notm}} 為您訂購的其他資源視需要指派與移除，例如虛擬伺服器實例或虛擬伺服器實例。我們不會一次只指派一個 IP 位址，我們會指派子網路。這表示有時會有更多空間給未來的資源使用。這項指定指出這些位址將由未來的資源使用。請參閱問題「**可以使用我看見的主要子網路所定義的其他 IP 位址嗎？**」以了解為何您不應該將這些 IP 位址視為可使用。


## 可以使用我看見的主要子網路所定義的其他 IP 位址嗎？
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

不！我們了解您將 {{site.data.keyword.BluSoftlayer_notm}} 指派的主要子網路視為任何其他子網路，但如 [關於子網路](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)中所述，主要子網路會隨需應變提供 IP 位址給資源。我們視需要指派及然後主要子網路，以期完成其他產品的工作。如果您試圖使用來自主要子網路的未指派 IP 位址，我們將在某個時刻無可避免地將它們指派給另一個資源。這會導致網路上發生 IP 衝突，以及一般的服務中斷。我們保留在完成其他產品工作時，封鎖主要子網路上未明確指派之任何 IP 位址，或以其他方式讓此 IP 位址無法使用的權力。您應該針對所有其他 IP 位址需要使用**次要子網路**，且我們強烈建議您將它們用於您的應用程式/服務位址需要。次要子網路的彈性高出許多，且只要您擁有它們，便會維護在您的帳戶上。


## 訂購時，可以指定我要將哪個子網路用於我的裝置嗎？
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

是的，可以在訂購處理程序期間指定特定的子網路。訂購裝置時，可以在訂單表格結尾提供此選項。選取專用 VLAN 之後，會呈現遞送至該 VLAN 的主要子網路清單。您可以選取想要的子網路。可以針對公用 VLAN 及子網路重複相同的處理程序。

很重要的一點是要注意提交訂單**不保證**在所要求的子網路中有 IP 位址可用。如果沒有位址可用，我們將會與您聯絡，以決定行動方針。為了得到最好的 {{site.data.keyword.BluSoftlayer_notm}} 體驗，會阻止針對一般用途選取子網路。


## 我用盡 IP 位址，怎麼辦？
{:#subnets-faq-ran-out-of-addresses}
{: faq}

這不會發生！我們會自動指派主要子網路，以讓更多 IP 位址可用來履行您的運算購買。您不需要管理任何事。不過，如果您的意思是您需要更多 IP 位址，例如用於本端虛擬機器或隔離應用程式，那麼請閱讀[關於子網路](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)中的**次要子網路**。


## 如何指派更多 IP 位址給運算資源？
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

首先，建議您購買**次要子網路**，有多種類型，因此請檢閱[關於子網路](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)。您的子網路遞送至想要的 IP 位址或 VLAN 之後，建議您參閱特定運算文件，以了解如何設定新的 IP 位址：

  * [裸機伺服器 IP 位址指派](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [虛擬伺服器實例 IP 位址指派](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## 我在查看子網路的 IP 位址時，`保留給 HSRP` 是什麼意思？
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

在越來越少的位置中，{{site.data.keyword.BluSoftlayer_notm}} 有路由器利用稱為「熱待命路由器通訊協定 (HSRP)」的技術。明確地說，它使用的方式會影響可用於***可攜式次要子網路*** 的 IP 位址；意思是您將失去對這些位置中兩個額外位址的存取權。在指定中，「保留給 HSRP」指出這些 IP 位址已保留來實現 HSRP 的需要。您甚至可以有子網路在相同的路由器上，有些有這樣的保留，有些則沒有。如同任何
IP 衝突，請不要試圖使用這些位址，否則您會有影響整個子網路上之資料流量的風險。

