---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-24"

keywords: custom server, {{site.data.keyword.baremetal_short}}, {{site.data.keyword.Bluemix_notm}}

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}


# 사용자 정의 베어메탈 서버 빌드
{: #ordering-baremetal-server}

다음 단계를 사용하여 사용자 정의 {{site.data.keyword.baremetal_long}}를 빌드하십시오.

## {{site.data.keyword.cloud_notm}} 카탈로그를 통한 프로비저닝
{: #provision-through-the-catalog}

{{site.data.keyword.cloud_notm}}를 통해 {{site.data.keyword.baremetal_short}}를 프로비저닝하려면 다음 단계를 사용하십시오.

1. [{{site.data.keyword.cloud_notm}} 카탈로그](https://cloud.ibm.com/catalog/){: external}를 여십시오.   
2. **컴퓨팅** 아래에서 {{site.data.keyword.baremetal_short}}를 선택하십시오.
3. 계속을 클릭하십시오. 계속 단추가 표시되지 않으면 로그인이 필요할 수 있습니다.
4. 프로비저닝할 **동일한** 서버의 **수량**을 입력하십시오. 기본값은 1입니다. 스펙이 _서로 다른_ 여러 서버를 프로비저닝하려면 각 서버를 따로 프로비저닝해야 합니다. 
5. **호스트 이름**은 서버의 영구 또는 임시 이름입니다(예: baremetal01). 형식화 세부사항을 보려면 **정보**를 클릭하십시오.
6. **도메인**은 인터넷에서 관리 제어를 정의하는 ID 문자열입니다(예: Customer-123456.cloud). 형식화 세부사항을 보려면 **정보**를 클릭하십시오.
7. **비용 청구**는 **시간별** 또는 **월별**입니다.
8. 서버가 놓일 **위치**(지역 및 데이터 센터)를 선택하십시오. 
9. 인증 서버(SAP 및 VMware)와 프로세서(단일, 듀얼 및 쿼드)의 목록을 보려면 **모든 서버**를 클릭하십시오. 워크로드에 가장 잘 맞는 서버를 선택하십시오.
10. **RAM**을 선택하십시오. 일부 서버의 경우 RAM 기본값은 CPU 모델에 따라 결정되며 이는 변경이 불가능합니다.  

SAP 인증 서버의 경우 RAM 및 운영 체제 기본값은 서버 선택사항에 따라 결정됩니다. 로컬 스토리지 옵션 기본값도 서버 선택사항에 따라 결정됩니다.
{ :note}

11. 프로비저닝 이후 서버에 로그인하는 데 사용할 수 있는 **SSH 키**의 선택적 공개 키를 입력하십시오.
12. 서버에 대한 **이미지**(운영 체제)를 선택하십시오. 사용자의 옵션은 선택한 서버에 따라 결정됩니다.
13. **추가 기능**을 펼쳐서 서버 구성과 관련된 옵션을 선택하십시오.
14. **스토리지 디스크**는 서버 선택사항에 따라 사전 구성됩니다. {{site.data.keyword.baremetal_short}}가 프로비저닝된 후에 파일 또는 블록 스토리지 볼륨을 추가하려면 **추가 기능** 펼치십시오.  
15. **네트워크 인터페이스** 아래에서 업링크 포트 속도와 사설 VLAN 옵션을 선택하십시오. **추가 기능**을 펼쳐서 적절한 옵션을 선택하거나 기본값을 사용하십시오.
16. 주문 요약에서 주문을 검토하십시오.
17. **프로모션 코드 적용** 아래에서 보유한 프로모션 코드를 입력하십시오.
18. 나열된 계약에 대해 서드파티 서비스 계약을 클릭하십시오. 
19. **작성**을 클릭하여 서버를 프로비저닝하십시오. 프로비저닝 주문 번호의 화면으로 경로 재지정됩니다. 이 화면은 영수증이기도 하므로 인쇄가 가능합니다. 

프로비저닝 주문 수신확인, 프로비저닝 주문 승인 및 처리, 프로비저닝 완료 등 일련의 이메일이 관리자에게 전송됩니다.

{{site.data.keyword.cloud_notm}}에 로그인할 수 있도록 _프로비저닝 완료_ 이메일에는 *디바이스 세부사항* 페이지에 대한 링크가 포함되어 있습니다. 또한 {{site.data.keyword.slportal}}에 직접 로그인할 수 있습니다.

견적서로 주문을 저장하거나 이를 추정값에 추가하는 옵션도 있습니다. 견적서를 저장하면 계정과 연관된 이메일 주소로 링크가 전송됩니다. 링크를 열어서 저장된 견적서 정보를 확인할 수 있습니다. 관리 > 비용 청구 및 사용량으로 이동하여 판매 > 디바이스 견적서를 선택하는 옵션도 있습니다. 액세스 권한이 있으면 견적서를 클릭하고 주문을 확인하여 제안된 견적서의 오퍼링을 구매할 수 있습니다. 추정값에 추가하면 가격 계산기에서 구성 제안 비용이 지정됩니다. 가격 계산기에 대한 세부사항을 보려면 **정보** 클릭하십시오.

## 고객 포털을 통한 프로비저닝
{{site.data.keyword.slportal}}을 통해 {{site.data.keyword.baremetal_short}}를 프로비저닝하려면 다음 단계를 사용하십시오.

1. 고유 인증 정보를 사용하여 [{{site.data.keyword.slportal}}](control.softlayer.com){: external}에 로그인하십시오.
2. **계정** > **주문하기**로 이동하십시오.
3. **시간별** 또는 **월별**을 선택하십시오.
3. 목록에서 {{site.data.keyword.baremetal_short}}가 배치될 데이터 센터를 선택하고 **시작 가격**을 클릭하여 인증 서버(SAP 또는 VMware) 또는 프로세서(단일, 듀얼 및 쿼드)를 선택하십시오.
4. 프로비저닝할 **동일한** 서버의 _수량_을 입력하십시오. 기본값은 1입니다. 스펙이 _서로 다른_ 여러 서버를 프로비저닝하려면 각 서버를 따로 프로비저닝해야 합니다. 
5. **RAM**을 선택하십시오. 일부 서버의 경우 RAM 기본값은 CPU 모델에 따라 결정되며 이는 변경이 불가능합니다.  

SAP 인증 서버의 경우 RAM 및 운영 체제 기본값은 서버 선택사항에 따라 결정됩니다. 로컬 스토리지 옵션 기본값도 서버 선택사항에 따라 결정됩니다.
{ :note}

6. 운영 체제를 선택하십시오.
7. 하드 드라이브 및 추가적인 시스템 추가 기능을 선택하십시오.
8. 경로 재지정된 **주문에 추가**를 클릭하여 주문을 확인하십시오. 
9. 서버에 대한 도메인 정보를 확인 또는 편집하십시오. **호스트 이름**은 서버의 영구 또는 임시 이름입니다(예: baremetal01).  
10. **클라우드 서비스 이용 약관** 및 **서드파티 서비스 계약**을 선택하십시오.
11. **프로모션 코드** 아래에서 보유한 프로모션 코드를 입력하고 **적용**을 클릭하십시오.
12. 지불 정보를 확인하거나 입력하고 **주문 제출**을 클릭하십시오. 프로비저닝 주문 번호의 화면으로 경로 재지정됩니다. 이 화면은 영수증이기도 하므로 인쇄가 가능합니다.  

프로비저닝 주문 수신확인, 프로비저닝 주문 승인 및 처리, 프로비저닝 완료 등 일련의 이메일이 관리자에게 전송됩니다. {{site.data.keyword.Bluemix_notm}}에 로그인한 이후 프로비저닝 완료 이메일에는 *디바이스 세부사항* 페이지에 대한 링크가 포함되어 있습니다. 또한 {{site.data.keyword.slportal}}에 직접 로그인할 수 있습니다.

## 다음 단계
{{site.data.keyword.baremetal_short}}가 프로비저닝된 후에 관리를 시작할 수 있습니다. 자세한 정보는 [{{site.data.keyword.baremetal_short}} 관리](/docs/bare-metal?topic=bare-metal-bm-manage-servers#bm-manage-servers)를 참조하십시오.
