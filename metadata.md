---
product: adobe experience manager
solution: Experience Manager
description: 컨설팅 Experience Manager 설명서
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.ko-KR
index: y
source-git-commit: e2dac4b36fb94d72b72ef6f73a77e3f566539444
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 54%

---


# 내부 사용을 위한 메타데이터

GitHub 제작 시스템의 메타데이터는 계층적이며 다음과 같이 증가하는 선례 수준으로 정의됩니다.

1. metadata.md
1. ToC
1. 문서

metadata.md 파일에 정의된 메타데이터는 전체 리포지토리에 적용되지만 ToC 및 문서 수준에서 재정의될 수 있습니다. 메타데이터 재정의는 가능한 한 낮은 수준에서 수행해야 합니다.

metadata.md

* `product`
* `git-repo`
* `index: y`

ToCs

* `sub-product`
* `user-guide-title`

문서

* `title`
* `description`

메타데이터에 대한 추가 정보는 [내부 작성 안내서](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).
