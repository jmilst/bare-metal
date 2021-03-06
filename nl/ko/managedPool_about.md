---

copyright:
  years:  2019
lastupdated: "2018-05-15"

keywrods: bare metal, managed pools

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 고객 관리 풀 정보
{: #bm-customer-managed-pools}

고객 관리 풀에서는 항상 조직에서 사용할 수 있는 서버 세트에 액세스할 수 있습니다. 해당 서버는 스펙에 맞게 구성됩니다. 필요할 때 풀에서 서버를 주문할 수 있습니다.

조직에서 사용량 최대 기간 중에 사용할 많은 수의 서버를 빈번히 프로비저닝해야 하는 경우에는 이 기능이 적합합니다. 이 기능을 사용하면 필요한 최소수의 서버만 사용할 수 있지만 추가 요구사항을 만족시키기 위해 언제나 다수의 서버 세트를 사용할 수 있습니다.

## 사용법 예제
{: #bm-managed-pools-use-case}

회사 A에서 일일 작업에 1000개의 활성 서버를 사용합니다. 그러나 최대 활동 시간에 500개의 추가 서버가 필요할 수 있습니다. 추가 서버를 신속하게 시작하고 실행해야 합니다.

요구사항을 충족시키기 위해 회사 A에서는 관리 서버 풀을 설정하기 위해 IBM에 문의합니다. 풀을 설정하고 나면 풀의 서버 수를 500으로 설정하기 위해 API를 호출합니다.

7월에 회사 A에는 풀에 있는 250개의 추가 서버가 필요합니다. 250개의 서버를 주문합니다. 이 주문은 풀에 있는 250개의 서버로 신속하게 이행됩니다. 주문이 완료되고 나면 250개의 서버가 회사 A의 관리 풀에 추가되므로 항상 500개가 사용 가능합니다.


## 다음 단계

조직에서 고객 관리 풀의 사용을 원하는 경우에는 [고객 관리 풀 프로비저닝](/bare-metal?topic=bare-metal-provisioning-customer-managed-pools)을 참조하십시오.
