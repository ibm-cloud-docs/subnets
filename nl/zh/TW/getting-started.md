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

# 開始使用子網路及 IP
{:#getting-started-subnets-ips}

子網路是您使用網際網路時很重要的一部分，使用 {{site.data.keyword.cloud}} 時也是如此。我們對於在平台上找到之子網路的類型和使用有特定的用語。每個子網路會以不同的方式提供 IP 位址給資源。您將遇到下列類型的子網路，深入瞭解每一種類型的子網路，即可瞭解如何在雲端基礎架構中最適當地使用它們。

  * 主要子網路 - 已指派以滿足其他產品 IP 定址需要的子網路，例如裸機伺服器和虛擬伺服器實例。這些子網路會自動指派及移除。
  * 次要子網路 - 由您購買及遞送的子網路，不再需要時會取消。有兩種子類型：
    * 可攜式 - IP 位址可用於 VLAN 上的所有資源。
    * 靜態 - IP 位址可用於識別為遞送端點的資源。
  * 廣域 IP 位址 - 利用 {{site.data.keyword.cloud}} 骨幹的獨特遞送行為，提供 IP 位址給識別為遞送端點的資源。

請在[關於子網路及 IP](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips) 中詳細檢閱各種類型，以便檢閱例如 IPv4 與 IPv6 以及公用/專用網路可用性等層面。

若要更一般性地瞭解子網路及子網路作業，請檢閱 [Subnetwork ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://en.wikipedia.org/wiki/Subnetwork)。此外，您會看到我們提及子網路時使用 [CIDR 表示法 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)。


## 訂購子網路
{:#ordering-subnets}

請遵循下列步驟，以訂購提供額外 IP 位址的子網路：

  1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/){: new_window}，然後登入帳戶。
  1. 在「客戶入口網站」導覽中，選取**標準基礎架構**。 
  1. 在「標準基礎架構」導覽中，選取**網路 > IP 管理 > 子網路**。
  1. 選取清單右上方的「新 IP 位址」鏈結。
  1. 若要開始訂購處理程序，請從圓鈕選取「公用」或「專用」子網路類型。
  1. 在 IPv4 或 IPv6 選項之間選擇。
  1. 若要選擇「靜態 IP」或「廣域 IP」，請按一下對應的方框。 
    1. 針對 IPv4，請使用「靜態」或「可攜式」選項中提供的下拉清單，選擇您要多少個位址。 
  1. 選取 VLAN 以建立新 IP 位址遞送到何處。
  1. 填寫所要求的剩餘資訊，然後按一下**建立**。


購買子網路之後，然後變更類型及遞送目的地。您必須訂購新的子網路，以獲得不同類型或遞送端點。

### 後續情形
{:#ordering-subnets-next}

除了任何必要的帳戶狀態核准處理程序，具有您所要配置的新子網路很快便會出現在您的帳戶上。
