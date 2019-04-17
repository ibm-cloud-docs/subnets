---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-04"

keywords: IP addresses , IP address, duration of your use

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# 關於子網路及 IP
{:#about-subnets-and-ips}

{{site.data.keyword.BluSoftlayer_notm}} 對於在平台上找到之子網路的類型和使用有特定的用語。知道其預期用途，將協助您知道如何在您的雲端基礎架構中最適切地使用它們。


## 子網路類型
{:#subnet-types}

### 主要子網路
{:#primary-subnets}

主要子網路會由 {{site.data.keyword.BluSoftlayer_notm}} 自動指派，它們也會視需要提供 IP 位址給資源。我們視需要指派及然後主要子網路，以期完成其他產品的工作。所有伺服器在佈建時至少會有一個來自主要子網路的 IP 位址，一般稱為主要 IP 位址。部分產品及選項會導致指派更多主要 IP 位址。

很重要的一點是要了解，主要子網路內的 IP 位址（尚未指派給資源）並不能提供您使用。如果您試圖使用來自主要子網路的未指派 IP 位址，我們將在某個時刻無可避免地將它們指派給另一個資源。這會導致網路上發生 IP 衝突，以及一般的服務中斷。我們保留在完成其他產品工作時，封鎖主要子網路上未明確指派之任何 IP 位址，或以其他方式讓此 IP 位址無法使用的權力。

我們**強烈建議**使用**次要子網路**作為您面對外界的服務/應用程式 IP 位址，尤其是在設計多伺服器應用程式時。使用已指派給您伺服器的主要 IP 位址完全沒有問題。不過，這麼做對於不確定伺服器取消及訂購的服務而言，會缺乏維護已知位址的彈性。關於主要 IP 位址指派的順序，例如遞增、遞減、跳過間隙等等，並沒有一定的保證。

無論如何，我們都無法保留「主要子網路」中的 IP 位址以供您使用。
{:note}

### 次要子網路
{:#secondary-subnets}

次要子網路提供您額外的 IP 位址以應付許多需要。不像主要子網路，這些子網路在您使用的期間由您擁有，且除非您取消它們否則不會移除。當您需要穩定的 IP 位址，且它不應該依賴任何特定運算裝置時，應該使用次要子網路。範例用途包括：

  * 您可以指派給自己的本端虛擬機器的 IP 位址。
  * 由單一伺服器管理的多個相異服務 IP 位址，容許您輕鬆地識別資料流量。常搭配 Web 伺服器及 TLS 使用。
  * 關聯於 DNS 的服務 IP 位址。在將工作負載移至新伺服器時要避免 DNS 快取延遲（亦即服務 IP 不會只因為伺服器的主要 IP 位址變更就變更）。
  * 利用「浮動」IP 位址通訊協定的高可用性配置。

為了達到這樣的用途，以及其他許多用途，我們為次要子網路提供不同的遞送選項。為了協助說明我們提供的次要子網路之間的差異，我們將在進一步的說明裡提及下面的範例子網路。

以下是子網路 10.0.0.0/29 所提供的 IP 位址範例：
```
10.0.0.0
10.0.0.1
10.0.0.2
10.0.0.3
10.0.0.4
10.0.0.5
10.0.0.6
10.0.0.7
```

#### 靜態子網路
{:#static-subnets}

靜態子網路提供單一目的地，以及對該子網路所定義之所有 IP 位址的存取。使用靜態子網路的一項好處是目的地裝置能夠利用所有已定義的 IP 位址，且不會遭受尋常的網路、閘道及廣播位址使用處罰。因此，使用我們的範例子網路，所有位址都是可以使用的：

```
10.0.0.0 - Usable by device
10.0.0.1 - Usable by device
10.0.0.2 - Usable by device
10.0.0.3 - Usable by device
10.0.0.4 - Usable by device
10.0.0.5 - Usable by device
10.0.0.6 - Usable by device
10.0.0.7 - Usable by device
```

因此，如果伺服器 IP 位址為 10.0.0.13，而您靜態地將 10.0.0.0/30 遞送至 10.0.0.13，該伺服器現在可以連結四個額外的 IP 位址；個別在每一個 IP 位址上接收資料流量。很重要的一點是瞭解不會對所提供的任何位址執行「網址轉換 (NAT)」。每個位址都可以原生地用於伺服器，因此每個都可以用於各自的用途。

|**可用性** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
|公用網路|是|是|
|專用網路|      |      |

#### 可攜式子網路
{:#portable-subnet}

可攜式子網路提供其 IP 位址給 VLAN 上的所有資源。這表示相同 VLAN 上的任何運算資源，可以利用子網路所提供的任何位址。此行為非常適用於多個資源之間的「浮動」位址，並使子網路與任何特定資源取消連結。可攜式子網路的必要性在於並非子網路所定義的所有 IP 位址都可供裝置使用。網路化機制需要耗用部分的 IP 位址。這些耗用的位址被稱為廣播、網路及閘道 IP 位址。請注意我們範例中可用的位址：

```
10.0.0.0 - Network
10.0.0.1 - Gateway
10.0.0.2 - Usable by devices
10.0.0.3 - Usable by devices
10.0.0.4 - Usable by devices
10.0.0.5 - Usable by devices
10.0.0.6 - Usable by devices
10.0.0.7 - Broadcast
```

|**可用性** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
|公用網路|是|是|
|專用網路|是|      |


### 廣域 IP 位址
{:#global-ip-addresses}

如需廣域 IP 供應項目的相關資訊，請參閱[廣域 IP 文件](/docs/infrastructure/subnets?topic=subnets-about-global-ip-address)。

|**可用性** | IPv4 | IPv6 |
| ---------------- | :--: | :--: |
|公用網路|是|是|
|專用網路|      |      |


## 取消子網路
{:#canceling-subnets}

如果您不再需要次要子網路，請遵循下列步驟來取消它：

  1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/){: new_window}，然後登入帳戶。
  1. 在「客戶入口網站」導覽中，選取**標準基礎架構**。 
  1. 從「標準基礎架構」導覽功能表，選取**網路 > IP 管理 > 子網路**。
  1. 選擇任何想要的過濾器以找到想要的子網路。
  1. 在子網路清單中，子網路項目的右手邊，會顯示有 X 的紅色圓圈。請按一下這個圖示，以起始取消處理程序。


## 訂購子網路時的產品特有考量
{:#product-specific-considerations-subnets}

### Hardware Firewall (Shared)
{:#hardware-firewall-subnets}

依預設，「可攜式子網路」不是透過防火牆保護。如果您需要此特性，請與業務代表進行討論。大於 /29 的次要子網路無法透過此防火牆供應項目遞送。

### 在伺服器之間轉移可攜式子網路 IP 位址
{:#transferring-portable-subnet-ip-between-servers}

將 IP 位址從某部伺服器轉移至另一部伺服器時，請確定傳送無償 ARP 封包。這容許我們的路由器更新 ARP 項目，並轉遞資料流量至正確的伺服器。不這麼做可能會導致在新伺服器收到轉移位址之資料流量時有最多 4 小時的延遲。

### Virtual Router Appliance
{:#virtual-router-appliances-subnets}

為高可用性 Virtual Router Appliance 之後的 VLAN 訂購子網路時，請確定子網路已正確地配置，容許兩部應用裝置之間進行失效接手。詳細的協助說明於 [VRA 高可用性配置](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-working-with-high-availability-and-vrrp)文件。
