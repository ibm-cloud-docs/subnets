---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# グローバル IP アドレスについて

グローバル IP は、サブネットを所有するアカウントに関連付けられている{{site.data.keyword.baremetal_short}}または{{site.data.keyword.virtualmachinesshort}}間で転送できる静的 IP アドレスです。グローバル IP は、{{site.data.keyword.BluSoftlayer_notm}} ネットワーク上の任意の互換デバイスに移動することができます。

グローバル IP アドレスは、IP の柔軟性を提供します。これによってユーザーは、サーバー間のワークロードを (異なるデータ・センターにあっても) 調整できるようになります。さらにグローバル IP は、サーバーと仮想サーバー・インスタンス (VSI) との間の遷移を考慮に入れることによって、IP 永続性を提供します。例えば、IP を特定のサーバーまたは VLAN に結び付けることなく、VSI から専用システムにアップグレードできます。

## グローバル IP アドレス (IP) を注文する方法

グローバル IP を注文するには、以下の手順に従ってください。

1. ブラウザーで[カスタマー・ポータル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://control.softlayer.com/){: new_window} を開き、ご使用のアカウントでログインします。
2. カスタマー・ポータル・ナビゲーションで、**「ネットワーク」>「IP 管理 (IP Management」>「サブネット」**を選択します。
3. **「IP アドレスの注文 (Order IP Addresses)」**リンクをクリックします。
4. ドロップダウン・メニューから、必要に応じて**「グローバル IPv4 (Global IPv4)」**または**「グローバル IPv6 (Global IPv6)」**を選択し、**「続行」**をクリックして注文プロセスを開始します。IP が、数分のうちに追加されます。

![図 1](images/1_2.png)
