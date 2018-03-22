---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 管理廣域 IP 位址

您可以在**子網路**畫面中管理「廣域 IP 位址」。 

1. 從瀏覽器中，開啟[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://control.softlayer.com/){: new_window}，然後登入帳戶。
2. 在「客戶入口網站」導覽中，選取**網路 > IP 管理 > 子網路**。
3. 在下拉功能表中，選擇**廣域 IPv4**（或 IPv6），以過濾「子網路」清單，使其僅顯示「廣域 IP」。
4. 按一下您要管理的「廣域 IP」。
 
  **附註：「廣域 IP」是可遞送至 IBM Cloud 網路內任何伺服器的靜態 IP 位址。現行靜態 IP 位址供應項目只能遞送至相同資料中心內的 IP 位址，但「廣域 IP 位址」未共用此限制。**

5. 在 IP 位址管理頁面上，輸入您要將「廣域 IP 位址」遞送至其中之伺服器的 IP 位址，並輸入任何適用的注意事項，然後選取**更新**。

![圖 2](images/2_1.png)

## 將廣域 IP 新增至伺服器 

必須先將「廣域 IP」適當地新增至系統，伺服器才會接受該 IP 的資料流量。每一個系統都需要略為不同的指令，以將它們顯示在接下來的幾個小節中。

### 針對 Linux 伺服器：

**Red Hat/CentOS**

1. 編輯（vim 或 nano）`/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* 新增下列幾行：
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. 編輯 `/etc/network/interfaces`

* 新增下列幾行：

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

如果您的系統未適當地運作，請改為新增下列各行，並將 # 取代為下一個可用的數字：

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### 針對 Windows 伺服器

1. 瀏覽至：**開始 -> 控制台 -> 網路連線 -> 區域連線（公用）（內容）**。
* 選取：**網際網路通訊協定 (TCP/IP)**，然後按一下**內容 -> 進階**。
* 選取 IP 位址區段中的**新增**，然後輸入 IP 位址及「子網路遮罩」。
* 此作業完成之後，只需要按一下「確定」就可以回到桌面。

若要驗證您的設定已生效，請瀏覽至**開始 -> 執行 -> "cmd"** 來開啟 DOS 提示，然後執行下列指令：

```
        > ipconfig /all
```

**附註：**

* 如果您在伺服器上已如同上面範例具有 `eth1:1` 檔案，請將最後一個數字增加為下一個可用的整數。
* 將廣域 IP 位址修改為新伺服器或 VSI 需要最多五分鐘的時間，才能生效。 
* 在 IBM Cloud 網路內，於 1 分鐘內就能更新遞送變更。
* 「廣域 IP」不適用於本端負載平衡器。
* 「廣域 IP」是從唯一的子網路進行配送；現有客戶 IP 不能轉換或用作「廣域 IP」。
* 「廣域 IP」本身不是自動失效接手解決方案，因為它們缺少性能檢查；不過，如果您要規避 DNS 傳播，則可以將「廣域 IP 位址」用作失效接手環境的元件。
