---
title: Veeva Vault 통합 알림
description: Veeva Vault 통합 알림
exl-id: 1a188671-d123-4475-a607-65743ba0dadd
source-git-commit: 07eab1e439626bd3bb3416c9e7d0c1666927a7aa
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# 우수 사례, 보호 및 알림

## 버전

이 통합에는 다음과 같은 최소 소프트웨어 버전이 필요합니다.

* Adobe Experience Manager, 6.5.5+
* Veeva Vault 프로모션 매트, 20R3.2+

## 데이터 개인정보 보호

이 통합은 Adobe Experience Manager과 Veeva Vault PromoMats 간에 콘텐츠를 전송하도록 설계되었습니다. 회사는 데이터 제어자로서 데이터의 수집 및 사용에 적용되는 개인정보 보호 법률 및 규정을 준수할 책임이 있습니다.

## 컨텐츠 동기화 빈도

통합 워크플로가 트리거되면 AEM 컨텐츠 및 메타데이터가 AEM에서 VVPN으로 동기화됩니다. 이 작업은 자동 또는 수동으로 수행할 수 있습니다. VVPM 메타데이터가 VVPM에서 AEM으로 동기화됩니다. 이 작업은 스케줄러를 통해 자동으로 수행하거나 버튼 클릭을 통해 수동으로 수행할 수 있습니다.

## 통합 제한 사항 및 우수 사례 및 보호 기능

이 통합을 사용할 때는 다음 제한 사항을 고려하십시오.

* 메타데이터 동기화 시 &quot;Text&quot; 및 &quot;Multiline Text&quot; 데이터 유형만 지원됩니다.
* 통합은 AEM 모듈식 콘텐츠(콘텐츠 조각 및 경험 조각)를 지원하지만 VVPM 모듈식 콘텐츠는 지원하지 않습니다.
* VVPM 연결 문서는 지원되지 않습니다.
* VVPM의 VVPM 시각적 주석을 AEM에 동기화할 수 없습니다.
* 통합은 VVPM에서 AEM으로 콘텐츠를 가져오지 않습니다.
* 메타데이터 유효성 검사가 지원되지 않습니다.
* 문서 수는 Veeva 라이센스에 따라 제한됩니다. [라이선스 제한](#veeva-license-limitations)을 참조하세요.
* API 호출 수는 Veeva 라이센스에 따라 제한됩니다. 자세한 내용은 [API 제한](https://developer.veevavault.com/docs/#what-are-rate-limits)을 참조하십시오. [라이선스 제한](#veeva-license-limitations)을 참조하세요.

## Veeva 라이센스 제한 사항

VVPM 일반 설정으로 이동하여 인스턴스 제한을 모니터링할 수 있습니다.

![Veeva 제한](assets/veeva-limits.png)
