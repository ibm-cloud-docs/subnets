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

# 關於廣域 IP 位址
{:#about-global-ip-address}

廣域 IP 位址是特殊化的靜態次要子網路。它以 /32 子網路（換句話說，單一 IP 位址）的形式交付給您，可以遞送至您帳戶上的任何其他 IP 位址。IPv4 和 IPv6 位址都可使用，且每個類型必須遞送到相同 IP 版本的 IP 位址。可接受的遞送目標包括您伺服器使用中的主要 IP 位址，以及任何可攜式次要子網路 IP 位址。廣域 IP 位址的獨特功能如下：

  * 廣域地隨需應變遞送至帳戶上的 IP 位址。
  * 位址由所有 {{site.data.keyword.cloud}} 邊緣路由器發表至網際網路。因此，您的資料會採取最短路徑到達 {{site.data.keyword.cloud}} 網路，而從那裡，您可以利用 {{site.data.keyword.cloud}} 專用全球骨幹抵達您配置的目的地。

廣域 IP 位址提供彈性。它們讓您能在伺服器之間移動工作負載，即使在地理位置不同的資料中心也是一樣。此外，廣域 IP 位址也藉由容許不需調整地轉移（例如，為了避免 DNS 快取）來提供 IP 持續性。廣域遞送功能最適合在災難回復站台之間轉移工作負載，或是平順地轉移至能更妥善服務您對象之地理區域裡的新部署。

|**可用性** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
|公用網路|是|是|
|專用網路|      |      |


## 管理廣域 IP 位址
{:#manage-global-ip-address}

若要管理廣域 IP 位址，請遵循下列步驟：

 1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/){: new_window}，然後登入帳戶。
 1. 在「客戶入口網站」導覽中，選取**標準基礎架構**。
 1. 在「標準基礎架構」導覽功能表中，選取**網路 > IP 管理 > 廣域 IP**。
 1. 您會看到列出您的廣域 IP 位址。請視需要利用過濾器來縮小搜尋範圍。 
 
您可能注意到部分項目沒有**目標**值，這指出廣域 IP 位址目前未遞送，因此它未提供服務。

### 遞送及取消遞送位址
{:#route-unroute-address}

一旦您找到想要的廣域 IP 位址，請按一下它的子網路 ID。您接下來將會看到一個畫面，顯示它目前適用的遞送目標。若要遞送（傳送資料流量）到新的目的地，您有兩個選項：

 * 輸入完整 IP 位址，或
 * 開始鍵入主機名稱。
 
鍵入主機名稱讓您能搜尋伺服器主機名稱，您便可以查閱其 IP 位址。輸入 IP 位址之後，請選取**更新**。若要取消遞送廣域 IP 位址，請選取**清除**。當輸入狀態變更為 'Unrouted'，請選取**更新**。

下拉功能表不是可用 IP 位址的詳盡清單。如果想要的 IP 位址無法從選項清單取得，請手動輸入。
{:note}

### 我多久可以更新一次？
{:#how-often-can-i-update}

在任何時刻，只允許有一個單一路徑更新在進行中。如果您試圖更新廣域 IP 位址的路徑，但有另一個更新正在進行中，則您會收到錯誤。請等待直到先前的更新完成，然後再重試。


## 如何訂購廣域 IP 位址
{:#how-to-order-global-ip-address}

請遵循下列指示，以訂購廣域 IP 位址：

  1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/){: new_window}，然後登入帳戶。
  1. 在「客戶入口網站」導覽中，選取**標準基礎架構**。
  1. 在「標準基礎架構」導覽功能表中，選取**網路 > IP 管理 > 廣域 IP**。
  3. 按一下**新 IP 位址**鏈結。
  4. 從下拉功能表中，視需要選擇**廣域 IPv4** 或**廣域 IPv6**，然後按一下**繼續**以開始訂購處理程序。

![圖 1](images/1_2.png)

### 後續情形
{:#global-ip-address-next}

除了任何必要的帳戶狀態核准處理程序，新廣域 IP 位址子網路很快便會出現在您的帳戶上。

### 資源限制
{:#global-ip-resource-limit}

帳戶針對每個 IP 版本只能有五 (5) 個廣域 IP 位址。例如，五 (5) 個 IPv4 廣域 IP 位址，以及五 (5) 個 IPv6 廣域 IP 位址。

## 如何取消廣域 IP 位址
{:#how-to-cancel-global-ip-address}

如果您不再需要廣域 IP 位址，請遵循下列步驟來取消它：

  1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/){: new_window}，然後登入帳戶。
  1. 在「客戶入口網站」導覽中，選取**標準基礎架構**。
  1. 在「標準基礎架構」導覽功能表中，選取**網路 > IP 管理 > 廣域 IP**。
  1. 完成任何必要的過濾器以找到想要的位址。
  1. 在位址清單中，位址項目的右手邊，會顯示具有 X 的圓圈。請按一下這個圖示，以起始取消處理程序。
