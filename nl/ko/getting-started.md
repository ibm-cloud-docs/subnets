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

# 서브넷 및 IP로 시작하기
{:#getting-started-subnets-ips}

서브넷은 인터넷 사용 방법의 중요한 부분이며 {{site.data.keyword.cloud}} 사용 시에도 마찬가지입니다. 플랫폼에 있는 서브넷의 유형과 사용에 맞는 특정 용어가 있습니다. 각 서브넷에서는 여러 다른 방법으로 리소스에 IP 주소를 제공합니다. 서브넷 유형은 다음과 같으며 서브넷의 각 유형에 대해 더 자세히 알면 클라우드 인프라에서 가장 잘 사용하는 방법을 이해할 수 있습니다.

  * 기본 서브넷 - Bare Metal Server 및 Virtual Server 인스턴스와 같은 다른 제품의 IP 주소 지정 요구 사항을 충족시키도록 할당된 서브넷. 해당 서브넷은 자동으로 지정되고 제거됩니다.
  * 보조 서브넷 - 사용자가 구매하고 라우팅하며, 더 이상 필요하지 않으면 취소한 서브넷. 하위 유형은 다음과 같이 두 가지가 있습니다.
    * 휴대용 - IP 주소를 VLAN의 모든 리소스에 사용할 수 있습니다.
    * 정적 - IP 주소를 라우팅 엔드포인트로 식별된 리소스에 사용할 수 있습니다.
  * 글로벌 IP 주소 - 고유한 라우팅 동작을 통해 라우팅 엔드포인트로 식별된 리소스에 IP 주소를 제공하는 {{site.data.keyword.cloud}}의 백본으로 활용합니다.

IPv4와 IPv6 및 공용/사설 네트워크 가용성 등의 요소를 검토하려면 [서브넷 및 IP 정보](/docs/infrastructure/subnets?topic=subnets-about-subnets-and-ips)에서 각 유형을 자세히 검토하십시오.

서브넷 및 서브넷 지정에 대한 더 일반적인 내용을 파악하려면 [서브네트워크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://en.wikipedia.org/wiki/Subnetwork)를 검토하십시오. 또한 [CIDR 표기법 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)을 사용하여 서브넷을 나타냅니다.


## 서브넷 주문
{:#ordering-subnets}

다음 단계를 따라 추가 IP 주소를 제공하는 서브넷을 주문하십시오.

  1. 브라우저에서 [고객 포털 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/){: new_window}을 열고 사용자 계정에 로그인하십시오.
  1. 고객 포털 탐색에서 **클래식 인프라**를 선택하십시오. 
  1. 클래식 인프라 탐색에서 **네트워크 > IP 관리> 서브넷**을 선택하십시오.
  1. 목록의 오른쪽 맨 위에서 "새 IP 주소" 링크를 선택하십시오.
  1. 주문 프로세스를 시작하려면 단일 선택 단추에서 공용 또는 사설 서브넷 유형을 선택하십시오.
  1. IPv4 또는 IPv6 옵션을 선택하십시오.
  1. 정적 또는 글로벌 IP를 선택하려면 해당 상자를 클릭하십시오. 
    1. IPv4의 경우 정적 또는 휴대용 옵션에서 사용 가능한 드롭 다운 목록을 사용하여 원하는 주소 수를 선택하십시오. 
  1. VLAN을 선택하여 새 IP 주소를 라우팅할 위치를 설정하십시오.
  1. 요청된 나머지 정보를 채우고 **작성**을 클릭하십시오.


서브넷을 구매하고 나면 유형과 라우팅 대상을 변경할 수 없습니다. 다른 유형 또는 라우팅 엔드포인트를 얻으려면 새 서브넷을 주문해야 합니다.

### 다음 작업
{:#ordering-subnets-next}

계정 상태의 필수 승인 프로세스를 금지하면 잠시 후에 원하는 구성의 새로운 서브넷이 계정에 표시됩니다.
