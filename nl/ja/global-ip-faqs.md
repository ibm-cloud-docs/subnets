---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-02-28"

keywords: Global IP FAQ, new Global IP, Global IP address

subcollection: subnets

---

{:faq: data-hd-content-type='faq'}
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# グローバル IP に関する FAQ
{: #global-ip-faq}


## 新しいグローバル IP を注文した後、その IP がアカウントに表示されるまで、どれくらいの時間がかかりますか?
{: #faq-global-ip-new-appear} 
{: faq}

グローバル IP は、注文した後、表示されるまで約 5 分かかります。


## 使用している既存の静的 IP をグローバル IP に変換できますか?
{: #faq-global-ip-convert-static-global} 
{: faq}

現時点ではできません。 {{site.data.keyword.BluSoftlayer_notm}} では、すべてのグローバル IP アドレスが新しいプロビジョン済み IP でなければならないため、既存の IP アドレスをグローバル IP に変換することは許可されていません。


## グローバル IP をインスタンスに関連付けるまで、どれくらいの時間がかかりますか?
{: #faq-global-ip-associate-instance} 
{: faq}

ご使用のグローバル IP を関連付けるまでの時間は、初めてグローバル IP を関連付けるか、またはグローバル IP を新規インスタンスに転送するかによって異なります。 新しいグローバル IP であれば、アドレスがインスタンスにリンクされるまで約 5 分かかります。 既存のグローバル IP をインスタンス間で転送する場合、1 分はかかりません。


## どのタイプのサブネットがグローバル IP で使用可能ですか?
{: #faq-global-ip-subnet-types} 
{: faq}

現時点で、グローバル IP アドレスは IPv4 アドレスと IPv6 アドレスの両方で提供されています。 グローバル IPv4 アドレスは単一 /32 アドレスとして有効ですが、グローバル IPv6 アドレスは単一 /64 アドレスとして有効です。


## IPv4 グローバル IP と IPv6 グローバル IP は交互に使用できますか?
{: #faq-global-ip-ipv4-ipv6-interchangeably} 
{: faq}

IP アドレス・スタイル間の非互換性により、IPv4 グローバル IP と IPv6 グローバル IP を交互に使用することは、選択肢に入っていません。


## グローバル IP とは何ですか?
{: #faq-what-is-global-ip} 
{: faq}

グローバル IP は、サブネットを所有するアカウントに関連付けられているベア・メタル・サーバーまたは仮想サーバー間で転送できる静的 IP アドレスです。 グローバル IP は、{{site.data.keyword.BluSoftlayer_notm}} ネットワーク上の任意の互換デバイスまたは互換インスタンスに移動することができます。


## グローバル IP アドレスはいくつまで注文できますか?
{: #faq-global-ip-how-many} 
{: faq}

アカウントごとに、5 個までの単一グローバル IP アドレスを使用できます。 グローバル IP は IPv4 または IPv6 のどちらでも、あるいは 2 つの組み合わせでもかまいません。


## グローバル IP をアカウントに追加するための料金は?
{: #faq-global-ip-how-much} 
{: faq}

グローバル IP の料金については、メインサイトにある製品明細を参照してください。 アドレスのタイプ (IPv4 アドレスおよび IPv6 アドレス) ごとのグローバル IP の料金については、該当する箇所までスクロールダウンしてください。
