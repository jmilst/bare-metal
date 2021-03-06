---

copyright:
  years: 2017, 2019
lastupdated: "2018-07-10"

keywords: raid, adaptec, ipmi, raid bios, raid array, RAID configuration

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Adaptec RAID 구성 작성 및 조정
{: #bm-create-raid-config}

Adaptec RAID BIOS를 사용하면 RAID 설정을 구성하고 관리할 수 있습니다. [OS 없음](/docs/bare-metal?topic=bare-metal-the-no-os-option) 옵션을 사용하고 있으며 특정 드라이브 구성을 설정하고자 하는 경우에 이 BIOS를 사용하십시오.

## IPMI 디바이스에 액세스하여 RAID BIOS와 상호작용
{: #bm-access-ipmi}

사용자의 시스템에 Adaptec 컨트롤러 또는 LSI 컨트롤러가 있는지에 상관없이 RAID BIOS와 상호작용하려면 IPMI를 사용하여 서버에 액세스해야 합니다. IPMI와 상호작용하려면 먼저 Adaptec {{site.data.keyword.cloud}} VPN에 연결해야 합니다.
1. [SSL](/docs/infrastructure/iaas-vpn?topic=VPN-setup-ssl-vpn-connections#setup-ssl-vpn-connections) 또는 PPTP를 사용하여 VPN에 로그인하십시오.
* [{{site.data.keyword.slportal}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/){: new_window}에서 디바이스 목록에 액세스하십시오. [디바이스 목록 액세스](/docs/infrastructure/vsi?topic=virtual-servers-managing-virtual-servers)를 참조하십시오.
* 액세스할 디바이스를 클릭하십시오.
* 서버 IPMI 액세스 세부사항을 찾으려면 원격 관리 탭을 선택하십시오.
* IPMI 디바이스의 IP를 브라우저에 입력하여 로그인하십시오.
* 원격 콘솔과의 상호작용을 시작하려면 **원격 제어 > 콘솔 경로 재지정**을 클릭하십시오.

## RAID 어레이 작성
{: #bm-create-raid-array}

시작 프로세스 중에 **Ctrl+A**를 눌러 RAID BIOS에 액세스하십시오.

시작하기 위해 RAID를 구성하면 논리 디바이스 구성(첫 번재 옵션)을 여십시오. 이 옵션을 선택하면 드라이브의 토폴로지가 스캔되고, 어레이를 관리하고, 어레이를 작성하며 기타 드라이브 관리 태스크를 완료할 수 있는 메뉴가 표시됩니다.

다음은 어레이를 작성하는 방법을 표시하는 예입니다. RAID 어레이 작성에 사용하는, 사용 가능한 드라이브 목록이 표시됩니다.

1. 드라이브를 선택하려면 스페이스바를 눌러 *선택된 드라이브* 상자를 채우십시오.
* 어레이에서 사용할 드라이브를 모두 선택한 후에 Enter를 눌러 RAID 구성 단계로 이동하십시오.
* 사용할 RAID 유형을 선택하십시오. 사용자의 요구사항에 최적인 RAID 설정을 찾는 중에 지원이 필요하면 다음의 [Adaptec FAQ ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.adaptec.com/en-us/_common/compatibility/_education/raid_level_compar_wp.htm){: new_window}를 참조하십시오.
* 구성하는 동안 어레이 레이블을 제공하십시오. 레이블에 RAID의 유형(예: RAID 10-A)을 포함하는 것이 좋습니다.
* **Enter**를 눌러 나머지 설정으로 이동하십시오. 기본값을 사용하십시오.

구성을 완료하고 완료를 선택하면 RAID가 작성됩니다. 기본 메뉴에서 '어레이 관리'를 선택하면 새 어레이를 볼 수 있습니다. 구성 유틸리티를 종료하려면 Adaptec BIOS를 종료하도록 프롬프트될 때까지 Esc 키를 누르십시오.

## 기존 RAID 어레이 제거
{: #bm-remove-raid-array}

기존 어레이를 제거해야 하는 경우 **어레이 관리**로 이동하여 제거할 어레이를 선택하고 **삭제**를 누른 다음 확인하십시오.

## 구성 예
{: #bm-example-config}

1. 총 여섯 개의 드라이브가 있는 서버에서 사용자의 운영 체제에 대한 RAID 0에 두 개의 SSD를 설정하고 사용자의 실제 데이터를 위해 RAID 10에 네 개의 추가 드라이브를 설정할 수 있습니다. 보조 어레이에 위치한 경우 이 구성을 사용하면 사이트 또는 서비스 데이터를 복원할 필요 없이 서버 OS를 신속하게 재로드할 수 있습니다.

* cPanel 서버의 경우, 별도의 SSD RAID 어레이에 /var 및 /home을 가질 수 있습니다. 해당 디렉토리는 cPanel 서버에서 가장 IO 집중적인 두 개의 디렉토리이므로 다음 설정을 사용하여 사이트 응답 시간을 잠재적으로 줄일 수 있습니다.
  * RAID 0 (2 SATA 드라이브) - /
  * RAID 0 (2 SSD 드라이브) - /var
  * RAID 0 (2 SSD 드라이브) - /home
  * RAID 10 (4 SATA 드라이브) - /backup

* 다중 논리 파티션을 설정하려면 단일 RAID 어레이를 사용하십시오. 예를 들어 RAID 1에 설정된 두 개의 4TB 드라이브를 사용하십시오. 다음 예를 참조하십시오.
  * 운영 체제용 100GB 1차 파티션
  * 사용자 데이터용 500GB 2차 파티션
  * 백업에 대한 나머지 공간의 3차 파티션