---
product: adobe experience manager
solution: Experience Manager
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
usetq: true
description: 컨설팅 Experience Manager 설명서
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.en
index: true
source-git-commit: e0159a3db7c79d12ee150be018ee5d005975b95a
workflow-type: tm+mt
source-wordcount: 94
ht-degree: 2%

---


# 내부 사용을 위한 메타데이터

GitHub 제작 시스템의 메타데이터는 계층적이며 다음과 같이 증가하는 선례 수준으로 정의됩니다.

1. metadata.md
1. 종료 날짜
1. 문서

metadata.md 파일에 정의된 메타데이터는 전체 리포지토리에 적용되지만 ToC 및 문서 수준에서 재정의될 수 있습니다. 메타데이터 재정의는 가능한 한 낮은 수준에서 수행해야 합니다.

metadata.md

* `product`
* `git-repo`
* `index: y`

Tocs

* `sub-product`
* `user-guide-title`

문서

* `title`
* `description`

메타데이터에 대한 추가 정보는 [내부 제작 안내서](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html)에서 찾을 수 있습니다.
