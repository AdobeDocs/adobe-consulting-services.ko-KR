---
title: Veeva Vault 통합 개요
description: Veeva Vault 통합 개요
exl-id: 52cc7290-b7e1-4476-877f-48934e6daf68
source-git-commit: 2e47baa4a255c34b3ca0b8631650dd5d8960fea8
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# Veeva Vault PromoMats 및 Adobe Experience Manager 통합 시작하기

이 통합은 업계 최고의 경험 제공 기능을 활용하면서도 컨텐츠를 관리하여 권한 및 규정 준수를 강화합니다.

이 통합에는 다음과 같은 최소 소프트웨어 버전이 필요합니다.

* Adobe Experience Manager, 6.5.5+
* Veeva Vault 프로모션 매트, 20R3.2+

>[!NOTE]
>
>통합을 위해 두 시스템 모두에서 서비스 사용자와 적절한 권한이 필요합니다.
>

>[!IMPORTANT]
>
>이 기능은 제품의 일부로 즉시 사용할 수 없습니다. 구현하려면 Adobe 컨설팅 유지 관리 계약이 필요합니다. 자세한 내용은 Adobe 담당자에게 문의하십시오.
>

## 원칙 및 기능

이 통합은 다음과 같은 두 가지 주요 사용 사례를 지원하기 위해 설계되었습니다.

1. 콘텐츠 승인 - AEM에서 새 콘텐츠를 만들거나 기존 콘텐츠를 편집한 경우, 콘텐츠가 생명 과학에 대한 의료, 법률, 규정(MLR) 승인 프로세스를 지원하는 VPM에서 사용하도록 승인되어야 합니다.
1. 컨텐츠 관리 - AEM에서 시작된 문서를 위해 AEM에서 생성된 디지털 전술(예: 이메일, 프레젠테이션, 웹 사이트)과 해당 요소(예: 로고, 사진, 그래픽) 간의 관계를 프로모션에서 설정하여 자산 활용에 대한 가시성을 제공합니다.

이점은 다음과 같습니다.

* 디지털 저장소 전체에서 중복되지 않고 에셋 및 콘텐츠에 대한 단일 소스 관리.
* 권한 및 규정 준수 관리를 위한 Veeva Vault와 동급 최고의 자산 및 컨텐츠 제작/제공을 위한 AEM을 모두 활용합니다.
* AEM과 Veeva Vault 간에 컨텐츠 및 메타데이터 이동을 자동화하는 데 도움이 됩니다.
* 승인 워크플로우용 Veeva에 콘텐츠를 전송하는 수작업을 줄입니다.
* 각 시스템은 강점에 맞게 사용되며 커넥터는 시스템 간에 콘텐츠를 자동으로 이동하여 출시 시간을 단축하는 데 도움이 됩니다.

통합은 어떤 작업을 수행합니까?

* AEM 사이트 페이지, 에셋, 콘텐츠 조각 및 경험 조각을 VPM으로 보낼 수 있습니다. AEM 페이지, 컨텐츠 조각 및 경험 조각을 스크린샷 PDF 또는 이미지로 보낼 수 있습니다. AEM Assets 바이너리는 그대로 전송됩니다.
* AEM에서 VVPM으로 구성할 수 있는 선택한 메타데이터 요소의 수동 및 자동 동기화를 지원합니다.
* VVPM에서 AEM으로 구성할 수 있는 선택한 메타데이터 요소의 수동 및 자동 동기화를 지원합니다.
* VVPM에서 AEM 사이트 페이지, 에셋, 콘텐츠 조각 및 경험 조각 간의 관계를 지원하여 콘텐츠 관계를 자동화합니다.
* 여러 디바이스 유형에 대한 렌디션 생성을 지원합니다.

>[!NOTE]
>
>구성 옵션에 대한 자세한 내용은 통합 사용 설명서 를 참조하십시오.
>

커넥터가 하지 않는 기능

* Veeva에서 AEM 프로세스 및 기능을 복제하지 않거나 그 반대로 복제하지 않습니다.
* MLR을 스스로 수행하지 않습니다. MLR이 발생하는 Veeva로 콘텐츠를 전송하는 것을 자동화하는 데 도움이 됩니다.
* AEM과 Veeva 간에 동일한 설정을 생성하는 데 사용하기 위한 것은 아닙니다. 모든 콘텐츠가 두 플랫폼 간에 이동할 필요는 없습니다.


>[!IMPORTANT]
>
>이 통합은 현재 AEM을 컨텐츠 동기화를 위한 소스로 간주합니다.

## 통합 가져오기

이 통합을 프로비저닝하려면 아래 단계를 수행해야 합니다.

통합을 요청하고 구성하려면 아래의 순서도와 순서도 세부 정보에 따라 하십시오.

![액세스 요청](assets/integration-request.png)

순서도 세부 정보(위의 단계로 매핑):

* **1단계** - Veeva Vault PromoMats 및 Adobe Experience Manager에 대한 라이센스가 이미 있거나 구매 중이라고 가정합니다.
* **2단계** - 통합을 활용하려면 Adobe 컨설팅과의 유지 보수 계약을 요약한 새 판매 주문(SO)에 서명해야 합니다.
* **3단계** - 통합 패키지를 설치하고 활성화하고 구성합니다.

## 지원

다음은 지원 팀에 문의하고 문제를 기록하는 방법에 대해 설명합니다.

### 통합 또는 Adobe Experience Manager 지원 요청

지원 티켓은 Adobe 고객 지원 센터에서 기록할 수 있습니다. Adobe Experience Cloud 관리자가에 로그온해야 합니다. [Adobe Admin Console](https://adminconsole.adobe.com/)에서 지원 탭을 클릭하고 사례를 만듭니다. 통합과 관련된 문제에 대해서는 다음 정보를 포함해야 합니다.

* **프로세스 제목**: `AEM - Veeva Vault Integration`
* **프로세스 소유자**: `Data Engineering`
* **설명**: `Description of the issue`
* **연락처**: `The email address(es) for relavant AEM point of contacts for your organization.`
* **AEM 인스턴스 URL**: `Place the Adobe Experience Manager instance url here.`
* **Veeva 인스턴스 URL**: `Place the Veeva Vault PromoMats instance url here.`

### Veeva Vault 프로모션 매트 지원 요청

경우에 따라 Veeva Vault PromoMats 인스턴스 작동에 문제가 발생할 수 있습니다. 이 경우 Veeva Vault PromoMatts 관리자는 지원 티켓을 만들라는 안내를 받을 수 있습니다. [Veeva 지원](http://support.veeva.com/). Veeva 인스턴스의 상태는 로 이동하여 볼 수 있습니다. [베바 트러스트](http://trust.veeva.com/).

