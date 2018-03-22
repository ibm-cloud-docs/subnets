---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 글로벌 IP 주소 관리

**서브넷** 화면에서 글로벌 IP 주소를 관리할 수 있습니다.  

1. 브라우저에서 [고객 포털 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com/){: new_window}을 열고 사용자 계정에 로그인하십시오. 
2. 고객 포털 탐색에서 **네트워크 > IP 관리 > 서브넷**을 선택하십시오. 
3. 드롭 다운 메뉴에서 **글로벌 IPv4**(또는 IPv6)를 선택하여 글로벌 IP만 표시하도록 서브넷 목록을 필터링하십시오. 
4. 관리하려는 글로벌 IP를 클릭하십시오. 
 
  **참고: 글로벌 IP는 IBM Cloud 네트워크 내의 모든 서버로 라우팅할 수 있는 정적 IP 주소입니다. 현재의
  정적 IP 주소 오퍼링은 동일한 데이터 센터 내의 IP 주소로만 라우팅될 수 있지만, 글로벌 IP 주소에는 이 제한사항이
  적용되지 않습니다.**

5. IP 주소 관리 페이지에서 글로벌 IP 주소를 라우팅하려는 서버의 IP 주소를 입력하고, 적용 가능한 모든 참고를 입력한 후 **업데이트**를 선택하십시오. 

![그림 2](images/2_1.png)

## 서버에 글로벌 IP 추가 

서버에서 글로벌 IP에 대한 트래픽을 허용하기 전에 IP가 시스템에 제대로 추가되어야 합니다. 각 시스템에 필요한 명령이 조금씩 다르므로 명령이 다음 몇 개 섹션에 표시됩니다. 

### Linux 서버의 경우:

**Red Hat/CentOS**

1. (vim 또는 nano) `/etc/sysconfig/network-scripts/ifcfg-eth1:1` 부분을 편집하십시오. 

* 다음 행을 추가하십시오. 
```
      DEVICE=eth1
      IPADDR=[Global IP address]
      NETMASK=255.255.255.255
      NETWORK=[Network of the Primary IP Block]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. `/etc/network/interfaces` 부분을 편집하십시오. 

* 다음 행을 추가하십시오. 

```
      post-up ip addr add [Global IP address]/32 dev eth1
      post-down ip addr del [Global IP address]/32 dev eth1
```

시스템이 제대로 작동하지 않는 경우 다음 행을 대신 추가하고 #을 사용 가능한 다음 숫자로 대체하십시오. 

```
        auto eth1:#

        iface eth1:# inet static

        address [Global IP address]

        netmask 255.255.255.255

        gateway [Server Primary Public Gateway]
```

### Windows 서버의 경우

1. **시작 -> 제어판 -> 네트워크 연결 -> 근거리 연결(공용) (특성)**을 찾아보십시오. 
* **인터넷 프로토콜(TCP/IP)**을 선택하고 **특성 -> 고급**을 클릭하십시오. 
* IP 주소 섹션에서 **추가**를 선택하고 IP 주소와 서브넷 마스크를 입력하십시오. 
* 이 태스크가 완료되면 "확인"을 클릭하여 데스크탑으로 돌아가십시오. 

설정이 적용되었는지를 확인하려면 **시작 -> 실행 -> "cmd"**를 찾아서 DOS 프롬프트를 열고 다음 명령을 실행하십시오. 

```
        > ipconfig /all
```

**참고:**

* 이미 위의 예제에서와 같이 서버에 `eth1:1` 파일이 있는 경우, 마지막 숫자를 다음으로 사용 가능한 정수로 늘리십시오. 
* 새 서버 또는 VSI로 글로벌 IP 주소로 수정하는 데는 최대 5분이 소요됩니다.  
* IBM Cloud 네트워크 내에서 라우트 변경은 업데이트하는 데 1분 미만이 소요됩니다. 
* 글로벌 IP는 로컬 로드 밸런서에서 작동하지 않습니다. 
* 글로벌 IP는 고유 서브넷에서 분배됩니다. 기존 고객 IP를 변환하거나 글로벌 IP로 사용할 수 없습니다. 
* 글로벌 IP는 성능 상태 검사가 부족하기 때문에 그 자체가 자동 장애 복구 솔루션이 아닙니다. 그러나 DNS 전파를 피하고 싶으면 글로벌 IP 주소를 장애 복구 환경의 컴포넌트로 사용할 수 있습니다. 
