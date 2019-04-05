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

# FAQ
{:#subnets-faq}

## サブネットの IP アドレスのところに表示される `Primary IP for future server only` とはどういう意味ですか?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

プライマリー・サブネットは、お客様から注文された他のリソース (ベアメタル・サーバーや仮想サーバー・インスタンスなど) のために、必要に応じて {{site.data.keyword.BluSoftlayer_notm}} によって割り当て/削除されます。IBM は単純に IP アドレスを一度に 1 つ割り当てるのではなく、サブネットを割り当てています。したがって、将来のリソース用に余地が残されることがあります。この表示は、そのようなアドレスが将来のリソースに使用される予定のものであることを明示しています。「**表示されているプライマリー・サブネットによって定義される他の IP アドレスは使用できますか?**」の質問を参照し、こうした IP アドレスを使用可能なものと見なしてはいけない理由を確認してください。


## 表示されているプライマリー・サブネットによって定義される他の IP アドレスは使用できますか?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

いいえ。{{site.data.keyword.BluSoftlayer_notm}} によって割り当てられたプライマリー・サブネットが他のサブネットと同じように表示されますが、[サブネットについて](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)で説明しているように、プライマリー・サブネットは、必要なときにリソースに対して IP アドレスを提供するためのものです。プライマリー・サブネットの割り当て/削除は、他の製品の注文を満たす目的で IBM が適宜行います。プライマリー・サブネットの範囲内の未割り当ての IP アドレスをお客様が使用すると、いつか IBM も同じ IP アドレスを別のリソースに割り当てることになります。その場合、ネットワークの IP 競合が発生し、広範囲でサービスが停止する可能性があります。IBM は、他の製品の注文を満たすときに明示的に割り当てられなかったプライマリー・サブネット上の IP アドレスをブロックする、あるいは使用できないようにする権利を保有します。追加の IP アドレスが必要になった場合には、**セカンダリー・サブネット**を使用する必要があります。お客様のアプリケーション/サービスのアドレス・ニーズにはセカンダリー・サブネットを使用することを強くお勧めします。セカンダリー・サブネットははるかに柔軟性が高く、お客様が所有している限り、お客様のアカウントに維持されます。


## デバイスを注文するときにデバイスで使用するサブネットを指定できますか?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

はい。注文プロセスの中で特定のサブネットを指定できます。デバイスを注文するとき、注文フォームの最後にこのオプションが表示されます。 プライベート VLAN を選択すると、その VLAN にルーティングされているプライマリー・サブネットのリストが表示されます。ご希望のサブネットを選択できます。パブリックの VLAN とサブネットについても同じプロセスを使用できます。

ただし、注文を送信したからといって、要求したサブネット内の IP アドレスが提供されることが**保証されるわけではない**ので注意してください。使用できるアドレスがない場合、IBM は対処方法について決定するためにお客様に連絡を取ります。{{site.data.keyword.BluSoftlayer_notm}} を最大限に利用できるように、一般的な使用にサブネットを選択することはお勧めしません。


## IP アドレスを使い切ってしまいました。どうすればよいですか?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

そのようなことは起こり得ません。お客様が購入したコンピュートを用意するために、IBM は自動的にプライマリー・サブネットを割り当て、追加の IP アドレスを提供します。お客様が管理する必要はありません。ただし、例えばローカル仮想マシンやアプリケーション分離などのために追加の IP アドレスが必要な場合は、[サブネットについて](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)の**セカンダリー・サブネット**を参照してください。


## コンピュート・リソースに追加で IP アドレスを割り当てるにはどうすればよいですか?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

まずは、**セカンダリー・サブネット**を購入します。タイプがいくつかあるので、[サブネットについて](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)を参照してください。目的の IP アドレスまたは VLAN にルーティングされるサブネットを取得したら、コンピュートの資料で新しい IP アドレスのセットアップ方法を確認してください。

  * [ベアメタル・サーバー IP アドレスの割り当て](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [仮想サーバー・インスタンス IP アドレスの割り当て](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## サブネットの IP アドレスのところに表示される `Reserved for HSRP` とはどういう意味ですか?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

ロケーションの数が減少する中、{{site.data.keyword.BluSoftlayer_notm}} には Hot Router Standby Protocol (HSRP) と呼ばれる技術を使用するルーターがあります。詳しく言うと、そのルーターの使用方法によって、***ポータブル・セカンダリー・サブネット***で使用できる IP アドレスが影響を受けます。つまり、それらのロケーションの 2 つの追加アドレスを使用できなくなります。宛先に「Reserved for HSRP」と表示されるのは、その IP アドレスが、HSRP の要件を満たすために予約済みであることを意味します。同じルーターでも、このような予約があるサブネットとないサブネットがある場合があります。他の IP 競合と同様に、こうしたアドレスを
使用しないでください。サブネット全体のトラフィックに影響を及ぼすリスクがあります。

