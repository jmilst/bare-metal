---

copyright:
  years: 2014, 2019
lastupdated: "2019-05-16"

keywords: bare metal, faq, {{site.data.keyword.cloud}}

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQ: Bare Metal Server
{: #bm-faq}

## UEFI 부팅 모드란 무엇입니까?
{: faq}
UEFI(Unified Extensible Firmware Interface)는 운영 체제와 펌웨어 간의 소프트웨어 인터페이스에 대한 스펙입니다. 

IBM BIOS 부트 모드에 대한 IBM Cloud 지원은 UEFI를 위해 단계적으로 폐지됩니다. 

UEFI에 대한 자세한 정보를 보려면 하드웨어 제조업체 문서를 참조하거나 [https://uefi.org/](https://uefi.org/)로 이동하십시오. 

## BIOS에서 비밀번호를 묻는 이유는 무엇입니까?
{: faq}

현재 {{site.data.keyword.cloud}}에서는 다양한 이유로 인해 BIOS에 대한 직접 액세스를 제공하지 않습니다. 그러나 BIOS를 변경할 수 있습니다. 부팅 순서를 포함하여 BIOS에서 수정이 필요한 사항이 있으면 [{{site.data.keyword.slportal}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/){: new_window}을 통해 지원 > 티켓 추가 아래에서 티켓을 작성하고 필요한 특정 변경사항을 요청하십시오. 

\*\*참고\*\* 이 경우, 서버를 다시 부팅해야 하므로 다시 부팅을 승인하도록 준비하고 변경을 수행할 시간 범위를 제공하십시오.

## 무료 OS 재로드를 제공합니까?
{: faq}

자동화된 OS 재로드는 무료이며 [{{site.data.keyword.slportal}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/){: new_window}을 통해 수행될 수 있습니다. 여기에는 사용자 정의된 OS 재로드(운영 체제 변경, 제어판/파티션 편집의 추가/제거 등)가 포함됩니다.  OS 재로드 수행에 대한 자세한 정보는 [OS 재로드 프로시저](/docs/infrastructure/software?topic=software-reloading-the-os)를 참조하십시오.


## Bare Metal Server의 기본 드라이브가 /dev/sdb로 표시됩니다. 무엇이 문제입니까?
{: faq}

IPMI의 가상 디스크가 /dev/sda 슬롯을 차지한 것이 원인일 수 있습니다. IPMIView에 연결하여 가상 미디어 탭을 찾아서 사용하지 않도록 안전하게 설정할 수 있습니다. **옵션 > 사용 안함**을 선택하고 **적용** 단추를 클릭하여 변경을 수행하십시오. {{site.data.keyword.baremetal_short}}가 다음에 다시 부팅될 때 기본 드라이브가 /dev/sda를 표시합니다.


## CPU 속도가 올바르지 않은 이유는 무엇입니까?
{: faq}

CPU 정보를 확인하려고 서버에 로그인한 경우 프로세서의 속도가 올바르지 않을 수 있습니다. 이 불일치는 EIST(Enhanced Intel SpeedStep Technology) 때문일 수 있습니다. EIST는 동적 빈도 스케일링 기술에 대해 Intel에서 사용하는 이름입니다.  이 기술은 다른 시스템에서는 *CPU 스로틀링* 또는 *버스 슬루잉*이라고도 합니다.  일부 AMD 시스템에는 *Cool'N'Quiet* 또는 *PowerNow!*라고 불리는 유사한 기술이 있습니다.  이러한 기술이 모두 동일하지는 않지만 CPU 속도를 느리게 하여 프로세서를 많이 사용하지 않는 경우에 전원 소모 및 열 생성을 줄이려는 동일한 목표를 가지고 있습니다.  서버를 재로드하는 경우 필요에 따라 클럭 속도를 높입니다.

서버의 Intel 프로세서가 SpeedStep 및 고객 포털을 지원하는지 확인하려면 고객 포털에서 다음 프로시저를 사용하십시오.
1. **디바이스**를 클릭하십시오.
* 목록에서 서버를 식별하십시오.
* 서버 이름을 클릭하여 **디바이스 세부사항**을 보십시오.
* **하드웨어**라는 서브섹션을 찾아서 서버의 프로세서 CPU 속도의 모델 번호를 찾으십시오.
* 서버 프로세서 모델 번호로 [Intel Processor Finder ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://processorfinder.intel.com/){: new_window}로 이동한 후에 이 번호를 사용하여 프로세서 관련 추가 정보와 Intel SpeedStep Technology의 지원 여부를 찾으십시오.

EIST는 검증된 기술입니다. 일반적으로 EIST를 끌 필요가 없습니다. 그러나 이 기능을 사용하지 않기로 결정한 경우, 지원 팀과 함께 티켓을 열어 이 기능을 사용하지 않도록 설정하십시오.  이 기능을 사용하지 않게 설정하면 서버가 다시 부팅됩니다.


## Bare Metal Server에 오래된 펌웨어가 있으면 어떻게 됩니까?
{: faq}

베어메탈 서버가 최적의 디바이스 호환성과 안정성을 갖도록 펌웨어를 지속적으로 업데이트하는 것이 중요합니다. {{site.data.keyword.baremetal_short}} 펌웨어 버전의 유효 기간이 지난 경우에는 디바이스 목록에서 베어메탈 서버를 선택하고 조치 메뉴에서 **펌웨어 업데이트**를 선택하여 펌웨어를 업데이트할 수 있습니다.

[{{site.data.keyword.slportal}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/){: new_window} 내에서 [OS 재로드](/docs/infrastructure/software?topic=software-reloading-the-os) 프로세스 중에 펌웨어 업데이트를 시작할 수 있습니다.

## 고객이 작업을 완료하면 Bare Metal Server의 드라이브는 어떻게 됩니까?
{: faq}

취소 시, 서버는 설정된 보유 시간 동안 자동으로 재확보 VLAN으로 이동합니다. 완료되면 재확보 프로세스가 시작되고 DOD 5250.22-M 알고리즘을 사용하여 드라이브가 삭제됩니다.  재확보는 드라이브의 일련 번호를 사용하여 추적합니다. 완료되고 나면 서버가 재할당을 위해 프로비저닝으로 이동합니다. 드라이브 오작동 시 수동 개입하도록 프롬프트가 표시되고 드라이브가 수명 종료로 설정됩니다.

오작동이 발생하거나 연령 또는 크기가 지원되지 않는 수준이면 수명 종료 프로세스가 시작됩니다. 해당 조건 중 하나가 발생하면 앞서 설명한 대로 드라이브가 삭제됩니다. 삭제 프로세스가 완료되면 디바이스를 깨거나 부수거나 조각 내어 물리적으로 영구 삭제합니다.  물리적 영구 삭제 프로세스는 드라이브의 일련 번호를 사용하여 추적합니다.

## 구매 가능한 베어메탈 서버를 알 수 있습니까?
{: faq}

예! 이제 베어메탈 서버의 프로비저닝 시에 어떤 서버가 어떤 데이터 센터에서 사용 가능한지 확인할 수 있습니다. 그러나 이 옵션은 시간별 오퍼링에만 사용할 수 있습니다. 월별 오퍼링으로는 서버 가용성을 볼 수 없습니다. 베어메탈 서버의 프로비저닝에 대한 자세한 정보는 [빠른 프로비저닝 서버에서 선택](/docs/bare-metal?topic=bare-metal-bm-select-popular-servers#bm-select-popular-servers)을 참조하십시오.

## 내 예약 베어메탈 서버에는 무엇이 포함됩니까?
{: faq}

CPU, RAM, 디스크 드라이브 및 RAID가 계약 기간 중에 예약에 포함되어 있습니다. 더 높은 네트워크 대역폭, 더 큰 스토리지 용량, 운영 체제 및 서드파티 소프트웨어가 필요하면 이러한 추가 기능은 월별로 비용이 청구됩니다.

## 내 예약 베어메탈 서버 계약이 끝나면 어떻게 됩니까?
{: faq}

클라우드 서비스는 계약 만료 시에 적용되는 비용으로 월별 서비스 기간에 지속됩니다.
