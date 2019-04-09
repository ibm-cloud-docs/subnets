---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP Address, Global IP addresses, Update button

subcollection: subnets

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# グローバル IP アドレスをデバイスにルーティング
{:#route-global-ip-address-device}

グローバル IP アドレスは、{{site.data.keyword.BluSoftlayer_notm}} が提供するどのデバイスに対しても、ユーザーによって手動でルーティングされます。 グローバル IP をデバイスにルーティングするには、そのデバイスが、そのグローバル IP を所有するアカウントに関連付けられている必要があります。 グローバル IP アドレスをデバイスにルーティングするには、以下の手順に従ってください。

1. [カスタマー・ポータル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/) で、「グローバル IP (Global IP)」画面にナビゲートします。 [『「グローバル IP (Global IP)」画面の表示』](/docs/infrastructure/subnets?topic=subnets-display-global-ip-screen){:new_window}を参照してください。
* ルーティングするグローバル IP サブネットを選択します。
* グローバル IP のルーティング先となるデバイスの IP アドレスを、**「ルーティング先 (Routes to)」**フィールドに入力していきます。 入力の進行に応じて、このフィールドは自動的に埋められます。 ここには、ご使用のアカウントに関連付けられているデバイスが表示されます。
* グローバル IP、デバイス、または他の項目に関する適切なメモを、**「メモ」**フィールドに入力します。
* **「更新」**ボタンを選択してルーティングを完了するか、またはアクションを取り消して**「サブネット」**画面に戻るには**「キャンセル」**を選択します。

## 次のステップ
{:#route-global-ip-address-device-next}

グローバル IP サブネット経路を開始すると、プロセスが開始されます。 ルーティングは一般に、完了までに 1 分はかかりません。 グローバル IP は、いつでもデバイスから[ルーティング解除](/docs/infrastructure/subnets?topic=subnets-unroute-global-ip-address)できます。
