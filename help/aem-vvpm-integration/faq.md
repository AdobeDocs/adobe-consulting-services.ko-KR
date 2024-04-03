---
title: Veeva Vault 통합 FAQ
description: Veeva Vault 통합 FAQ
exl-id: c308ebb3-7881-4094-9f35-c67a96fb5ab1
source-git-commit: e4a5e55ac9b79a8de7dfa8ddd3d0ad99560917b8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# 자주 묻는 질문

**어떤 메타데이터를 Veeva에 동기화해야 합니까?**

Veeva Portal의 콘텐츠 유형(예: 프로모션)에 따라 메타데이터를 이해하는 것이 중요합니다. Veeva 포털을 검토한 후 각 에셋/페이지에 대한 관련 메타데이터를 모두 저장하도록 AEM에서 콘텐츠 메타데이터 스키마를 구성하고, 두 시스템 간에 메타데이터를 매핑하도록 통합을 구성합니다.

**통합이 Veeva 연결 문서를 지원합니까? 그렇지 않으면 어떤 관계 유형이 지원됩니까?**

아니. 다음을 참조하십시오 [Veeva 설명서](https://vaulthelp2.vod309.com/wordpress/admin-user-help/documents-admin-user-help/about-document-relationships/). 연결된 문서(참조 관계 유형)는 특수한 자격 증명 모음 동작이 있으므로 API를 통해 만들거나 삭제할 수 없는 표준 관계 유형 중 하나입니다. 이 목록에 없는 구성 요소, 지원 문서 등은 AEM Veeva Cloud 구성을 통해 구성할 수 있어야 합니다.

**통합은 AEM 모듈식 콘텐츠를 지원합니까?**

예. 통합은 AEM 콘텐츠 조각 및 경험 조각을 지원합니다.

**이 통합은 Veeva 모듈식 콘텐츠를 지원합니까?**

아뇨, 지금은 아니에요.

**통합에서 Veeva 시각적 주석을 AEM에 동기화합니까?**

아뇨, 지금은 아니에요. 시각적 주석은 API를 PDF으로 통해서만 액세스할 수 있습니다.

**통합으로 동기화된 VVPM 문서에 대한 권한을 설정하려면 어떻게 합니까?**

통합에서는 서비스 사용자를 사용하여 API를 통해 문서를 업로드합니다.  문서 기본값 설정 및 오버라이드 규칙(문서의 기본값 설정 역할)은 VPM 사용자 인터페이스에서만 지원되며 API를 사용할 때는 적용되지 않습니다. 역할 할당에 DAC(Dynamic Access Control)를 사용하는 것이 좋습니다. DAC는 API를 포함한 모든 터치 포인트를 통해 적용됩니다. [여기에서 설명서를 참조하십시오.](http://vaulthelp2.vod309.com/wordpress/admin-user-help/ah-user-permissions-access-control/about-dynamic-access-control-for-documents/)

**통합에서 여러 VVPM 인스턴스를 지원합니까?**

통합에서는 여러 Veeva 끝점을 하나의 AEM 인스턴스에서 구성할 수 있는 클라우드 구성 접근 방식을 사용합니다.

**통합은 AEM 게시를 지원합니까?**

아니요. 이 통합은 AEM 작성자에서만 작동합니다. 콘텐츠가 게시되기 전에 MLR 검토 주기를 용이하게 하기 위한 것입니다.
