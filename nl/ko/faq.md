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

## 서브넷의 IP 주소를 확인할 때 표시되는 `향후 서버 전용 기본 IP`가 의미하는 내용은 무엇입니까?
{:#subnets-faq-primary-ip-future-server-only}
{: faq}

주문한 기타 리소스(예: Bare Metal Server 또는 Virtual Server 인스턴스)용으로 {{site.data.keyword.BluSoftlayer_notm}}에 필요한 대로 기본 서브넷을 할당하고 제거합니다. 단순히 한 번에 하나의 IP를 지정하지 않고 서브넷을 지정합니다. 즉, 경우에 따라 향후 리소스에 사용할 여분이 있습니다. 이와 같이 지정하면 주소를 향후 리소스에 사용하게 됩니다. 이 IP 주소를 사용 가능한 것으로 간주하지 않아야 하는 이유를 확인하려면 "**표시되는 기본 서브넷에 정의된 다른 IP 주소를 사용할 수 있습니까?**"라는 질문을 참조하십시오.


## 표시되는 기본 서브넷에 정의된 다른 IP 주소를 사용할 수 있습니까?
{:#subnets-faq-use-other-ip-addresses-primary-subnets}
{: faq}

아니오! {{site.data.keyword.BluSoftlayer_notm}}에서 지정한 기본 서브넷이 다른 서브넷으로 표시된다는 점을 발견했습니다. 그러나 [서브넷 정보](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)에 설명된 대로 기본 서브넷은 요청 시 리소스에 IP 주소를 제공하는 데 사용합니다. 다른 제품을 이행하기 위해 필요한 대로 기본 서브넷을 지정하고 제거합니다. 사용자가 기본 서브넷에서 지정되지 않은 IP 주소를 사용하려고 하면 당사에서 일정 시점에 다른 리소스에 해당 주소를 지정합니다. 그러면 네트워크에서 IP가 충돌하고 일반 서비스가 중단됩니다. IBM에서는 기타 제품을 이행하는 중에 특별히 지정되지 않은 기본 서브넷의 IP 주소를 차단하거나 사용 불가능하게 조치할 권한이 있습니다. 추가 IP 주소가 필요할 때마다 **보조 서브넷**을 사용해야 하며 애플리케이션/서비스 주소가 필요할 때 사용하는 것이 좋습니다. 보조 서브넷은 유연성이 훨씬 뛰어나며 사용자가 소유하는 동안 계속 계정에서 유지보수됩니다.


## 디바이스를 주문할 때 내 디바이스에 대해 사용할 서브넷을 지정하는 방법이 있습니까?
{:#subnets-faq-specify-which-subnet-on-order}
{: faq}

예. 주문 프로세스 중에 특정 서브넷을 지정할 수 있습니다. 디바이스 주문 시, 이 옵션은 주문 양식의 끝 부분에 있습니다. 사설 VLAN을 선택하고 나면 해당 VLAN으로 라우팅된 기본 서브넷 목록이 표시됩니다. 원하는 서브넷을 선택할 수 있습니다. 공용 VLAN 및 서브넷에 동일한 프로세스를 반복할 수 있습니다.

주문을 제출한다고 해서 요청된 서브넷에서 IP 주소를 사용할 수 있다고 **보장하지 않는다는 점**을 참고하십시오. 주소를 사용할 수 없으면 수행한 일련의 조치를 판별하기 위해 사용자에게 연락합니다. 최상의 {{site.data.keyword.BluSoftlayer_notm}} 경험을 제공하기 위해 일반적인 용도로는 서브넷을 선택하지 않는 것이 좋습니다.


## IP 주소가 부족합니다. 어떻게 해야 합니까?
{:#subnets-faq-ran-out-of-addresses}
{: faq}

이 문제는 발생하지 않아야 합니다! 컴퓨팅 구매를 이행하는 데 추가 IP 주소를 사용할 수 있도록 당사에서 기본 서브넷을 자동으로 지정합니다. 사용자가 관리할 필요가 전혀 없습니다. 그러나 로컬 가상 머신용이나 애플리케이션 분리 용도로 추가 IP 주소가 필요한 것이라면 [서브넷 정보](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)의 **보조 서브넷**의 내용을 읽어 보십시오.


## 컴퓨팅 리소스에 추가 IP 주소를 지정하는 방법은 무엇입니까?
{:#subnets-faq-assign-more-ip-addresses-to-compute-resource}
{: faq}

먼저 **보조 서브넷**을 구매하려고 하며 여러 유형이 있으므로 [서브넷 정보](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)를 검토하십시오. 원하는 IP 주소나 VLAN으로 라우팅되는 서브넷이 있으면 새 IP 주소를 설정하는 방법에 관한 특정 컴퓨팅 문서를 참조할 수 있습니다.

  * [Bare Metal Server IP 주소 지정](/docs/bare-metal?topic=bare-metal-assigning-server-ip-addresses)
  * [Virtual Server 인스턴스 IP 주소 지정](/docs/vsi?topic=virtual-servers-assigning-server-ip-addresses)


## 서브넷의 IP 주소를 확인할 때 표시되는 `HSRP에 예약됨`이 의미하는 내용은 무엇입니까?
{:#subnets-faq-reserved-hsrp-meaning}
{: faq}

점점 줄어드는 위치에서 {{site.data.keyword.BluSoftlayer_notm}}에는 Hot Router Standby Protocol 또는 HSRP라고도 하는 기술을 활용하는 라우터가 있습니다. 특히 사용 방식은 ***휴대용 보조 서브넷***에 사용 가능한 IP 주소에 영향을 미칩니다. 즉, 이 위치에서는 두 개의 추가 주소에 대한 액세스 권한이 유실됩니다. "HSRP용으로 예약"이라고 지정되어 있으므로 이 IP 주소는 HSRP의 요구사항을 이행하는 데 사용하도록 예약되어 있습니다. 일부는 이와 같이 예약되어 있고 일부는 예약되어 있지 않은 서브넷이 동일한 서브넷에 있을 수 있습니다. IP 충돌 등이 발생할 수 있으므로 이 주소를 사용하려고 시도하지 마십시오.
그렇지 않으면 전체 서브넷의 트래픽에 영향을 미칠 위험이 있습니다.

