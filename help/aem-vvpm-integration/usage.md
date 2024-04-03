---
title: Veeva Vault 통합 사용
description: Veeva Vault 통합 사용
exl-id: efff7af1-eb25-4a1d-b7ef-52e3336970ff
source-git-commit: 19949a48cfee0c17481e52f286a460e9d81d7ff0
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# 통합 사용

## 연습

다음 비디오 연습에서는 커넥터 사용에 대해 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/332137/?quality=12&learn=on)

## 설정

이 안내서에서는 커넥터를 시작하고 실행하는 과정을 안내합니다.

>[!IMPORTANT]
>
>각 시스템에 대해 다음 단계는 **관리자** 각 시스템에 대해.
>
>이 설명서의 단계는 권한 및/또는 관리자 액세스 권한을 지정하는 것과 관련된 통합/등록을 만드는 과정을 안내합니다.  이러한 단계는 수행하기 전에 회사 정책을 준수하고 신중하게 수행해야 합니다.
>

### 통합 패키지 설치

통합 AEM 패키지에 대한 액세스 권한을 받습니다. 통합을 설치하는 두 가지 옵션이 있습니다.

1. **패키지 설치** - 직진하고 덜 관여함.
2. **POM 설치** - 고급 기능이 있지만 AEM Cloud Manager를 사용하고 통합을 업그레이드할 때 유용할 수 있습니다.

#### 패키지 설치

패키지를 설치하려면 온보딩 이메일에 제공된 링크로 패키지를 다운로드합니다. [AEM 패키지 설치에 대한 자세한 지침은 여기를 클릭하여 확인할 수 있습니다.](https://experienceleague.adobe.com/docs/experience-manager-64/administering/contentmanagement/package-manager.html?#installing-packages)

#### POM 설치

POM에 커넥터를 포함하려면 다음 단계를 따르십시오. 사용자 이름 및 암호를 온보딩 이메일에서 받은 사용자 이름 및 암호로 바꿉니다.

1. 다음에 추가 `.cloudmanager/maven/settings.xml` 프로젝트의 파일 또는 `~/.m2/settings.xml` 컴퓨터에서. 바꾸기 `YOUR_USERNAME` (사용자 이름 및 `YOUR_PASSWORD` (온보딩 이메일에 입력한 암호 포함)

   >[!IMPORTANT]
   >
   >Cloud Manager를 사용하는 경우 보안 접근 방식은 다음에 대한 여기에서 제공하는 단계를 따릅니다. [암호로 보호된 Maven 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories).
   >

   ```
   <settings>
       ...
       <servers>
           ...
           <server>
               <id>repo.ea.adobe.net</id>
               <username>YOUR_USERNAME</username>
               <password>YOUR_PASSWORD</password>
               <filePermissions>BucketOwnerFullControl</filePermissions>
               <configuration>
                 <wagonProvider>s3</wagonProvider>
               </configuration>
           </server>
           ...
       </servers>
       ...
   </settings>
   ```

2. 프로젝트의 다음 항목 추가 `pom.xml` 파일:

   ```
   <project>
       ...
       <build>
           ...
           <extensions>
               ...
               <extension>
                   <groupId>com.allogy.maven.wagon</groupId>
                   <artifactId>maven-s3-wagon</artifactId>
                   <version>1.2.0</version>
               </extension>
               ...
           </extensions>
           ...
       </build>
       ...
       <repositories>
           ...
           <repository>
               <id>repo.ea.adobe.net</id>
               <url>s3://repo.ea.adobe.net/release</url>
               <releases>
                   <enabled>true</enabled>
               </releases>
           </repository>
           ...
       </repositories>
       ...
   </project>
   ```

3. 프로젝트의 다음 항목 추가 `all/pom.xml` 파일. 바꾸기 `project.dependencies.dependency.version` 적절한 버전 및 `project.build.plugins.plugin.configuration.embeddeds.embedded.target` 를 입력합니다.

   ```
   <project>
       ...
       <build>
           ...
           <plugins>
               ...
               <plugin>
                   <groupId>org.apache.jackrabbit</groupId>
                   <artifactId>filevault-package-maven-plugin</artifactId>
                   ...
                   <configuration>
                       ...
                       <embeddeds>
                           ...
                           <embedded>
                               <groupId>com.adobe.acs.aemveeva</groupId>
                               <artifactId>aem-veeva-connector.all</artifactId>
                               <type>zip</type>
                               <target>/apps/APP_NAME-packages/application/install</target>
                           </embedded>
                           ...
                       </embeddeds>
                   </configuration>
               </plugin>
               ...
           </plugins>
           ...
       </build>
       ...
       <dependencies>
           ...
           <dependency>
               <groupId>com.adobe.acs.aemveeva</groupId>
               <artifactId>aem-veeva-connector.all</artifactId>
               <version>1.0.5</version>
               <type>zip</type>
           </dependency>            
           ...
       </dependencies>
       ...
   </project>
   ```

### 클라우드 구성

이 통합은 커넥터가 작동할 폴더에 클라우드 구성을 만들어 구성되었습니다. 다음 단계에 따라 클라우드 구성을 만듭니다.

1. Veeva 클라우드 구성으로 이동합니다.

   ![클라우드 구성으로 이동](assets/cloud-config-navigate.png)

2. 적절한 폴더에 새 Veeva 클라우드 구성을 생성하고 다음 섹션에 설명된 대로 을 채웁니다.

   ![클라우드 구성 만들기](assets/cloud-config-create.png)

#### 구성 탭

구성 탭에서 다음을 입력합니다.

![구성 탭](assets/configuration-tab.png)

1. 필수. Veeva Vault 커넥터 구성 제목 이는 임의의 값이 될 수 있습니다. (예: `Veeva Vault Configuration`)
2. 필수. Veeva 인스턴스의 도메인 url(예: `https://my-instance.veevavault.com/`)
3. 필수. Veeva Vault API를 호출하는 데 필요한 ClientID. 이 값은 임의의 값이 될 수 있으며 대부분 디버깅에 사용됩니다. (예: `adobe-aem-vvtechpartner`)
4. 필수. Veeva Vault 사용자 이름. 다음을 참조하십시오 [사용자 생성 정보](#veeva-user-creation).
5. 필수. Veeva Vault 암호입니다. 다음을 참조하십시오 [사용자 생성 정보](#veeva-user-creation).

#### Adobe IO 탭

프로젝트가 페이지에 대한 PDF 또는 이미지를 생성해야 하는 경우 이 탭이 필요합니다. adobe io 탭에서 다음을 입력합니다.

![Adobe IO 탭](assets/adobe-io-tab.png)

1. 필수. 온보딩 이메일에 제공된 PDF 이미지를 만들기 위한 Adobe IO 엔드포인트. (예: `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/trigger-action.json`)
2. 필수. 페이지 이미지 생성을 위한 작업 이름입니다. 이 값은 다음과 같아야 합니다. `aem-veeva-integration/get-image-async`.
3. 필수. HTML 이미지 생성을 위한 작업 이름입니다. 이 값은 다음과 같아야 합니다. `aem-veeva-integration/get-pdf-async-new`.
4. 필수. 온보딩 이메일에 제공된 생성 상태를 가져오기 위한 Adobe IO 엔드포인트.(예: `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/get-state-value`)
5. 필수. Adobe IO에서 사용할 AEM 사용자 이름입니다. 다음을 참조하십시오 [AEM 사용자 생성](#aem-user-creation).
6. 필수. Adobe IO에서 사용할 AEM 암호입니다. 다음을 참조하십시오 [AEM 사용자 생성](#aem-user-creation).
7. 선택 사항입니다. 기본 시간 제한은 AIO 서비스가 응답 가져오기를 중지하는 지정된 시간까지 페이지가 응답할 수 있도록 하는 것입니다. 기본값은 입니다. `30000`.
8. 선택 사항입니다. 지연은 스크린샷을 찍기 전에 모든 이미지를 렌더링하기 위해 페이지가 200으로 응답한 이후입니다. 기본값은 입니다. `2000`.
9. 선택 사항입니다. 스크린샷/PDF 생성 URL은 구성된 값(초) 이후 만료됩니다.
10. 선택 사항입니다. Adobe IO 스크린샷/PDF 생성 서비스가 비동기화됩니다. AEM 서비스는 AIO 상태 엔드포인트를 호출하여 스크린샷/PDF을 가져옵니다. 이 속성은 각 상태 호출 간의 일시 중지를 밀리초 단위로 결정합니다. 기본값은 입니다. `10000`.
11. 선택 사항입니다. 스크린샷/PDF 가져오기를 위한 Adobe IO에 대한 상태 호출의 최대 재시도 횟수. 기본값은 입니다. `10`.

#### 고급 탭

고급 탭에서 다음을 입력합니다.

![고급 탭](assets/advanced-tab.png)

1. PDF/이미지 생성에 필요합니다. PDF/이미지를 만들 때 사용되는 파일 이름 패턴입니다. `{name}` 템플릿으로 만들 수 있습니다. (예: `{name}-screenshot`)
2. 선택 사항입니다. 데스크탑 이외의 필요한 페이지 스크린샷에 대한 장치 유형입니다. 유효한 유형은 다음과 같습니다. `Tab (iPad)`, 및 `Mobile (iPhone X)`.
3. 선택 사항입니다. 위 렌디션을 나타내는 Veeva의 렌디션 유형 값입니다. (예: `web_ready__c`)
4. PDF/이미지 생성에 필요합니다. 생성할 스크린샷 유형입니다. 다음 중 하나 `PDF` 또는 `Image`.
5. PDF/이미지 생성에 필요합니다. 생성할 PDF 유형입니다. 다음 중 하나 `Print CSS Based PDF` 또는 `Pixel Perfect Screenshot PDF`.
6. PDF/이미지 생성에 필요합니다. 생성할 이미지 유형입니다. 다음 중 하나 `PNG` 또는 `JPEG`.
7. 필수. Veeva Vault 승인 트리거가 실행되면 실행할 워크플로우입니다.
8. 필수. 승인됨을 나타내는 상태 속성 값입니다. (예: `Approved for Distribution`)
9. 필수. Veeva Vault 거부 트리거가 실행되면 실행할 워크플로우입니다.
10. 필수. 거부됨/승인되지 않음 을 나타내는 상태 속성 값입니다. (예: `Rejected`)
11. 선택 사항입니다. Veeva Vault의 문서 ID에 대한 속성 이름입니다. 기본값은 입니다. `id`.
12. 선택 사항입니다. Veeva Vault의 상태에 대한 속성 이름입니다. 기본값은 입니다. `status__v`.
13. 선택 사항입니다. 문서 수정 날짜의 속성 이름입니다. 기본값은 입니다. `version_modified_date__v`.
14. 선택 사항입니다. 문서 리소스 URL의 속성 이름입니다. 기본값은 입니다. `external_id__v`. 이 필드가 이미 사용 중이면 Veeva에서 다른 필드를 만들고 여기에서 필드 이름을 채웁니다. 이 필드는 AEM 리소스 경로를 보유하기 위해 Veeva에서 사용됩니다. 이 단계는 자동화된 메타데이터 동기화에 필요합니다.
15. 선택 사항입니다. Veeva Vault의 주요 버전 번호에 대한 속성 이름입니다. 기본값은 입니다. `major_version_number__v`.
16. 선택 사항입니다. Veeva Vault의 부 버전 번호에 대한 속성 이름입니다. 기본값은 입니다. `minor_version_number__v`.
17. 선택 사항입니다. Veeva Vault 관계 유형 값입니다. 페이지에 추가된 모든 에셋은 이 값을 기반으로 관련 에셋으로 표시됩니다. 기본값은 입니다. `supporting_document__c`.

#### 페이지 탭

페이지를 동기화하는 경우 페이지 탭에 다음을 입력합니다.

![페이지 탭](assets/page-tab.png)

1. 필수. AEM에서 Veeva로 속성을 매핑합니다.
a. AEM 속성 이름. AEM 속성에서 선택할 수 있습니다. (예: `jcr:title`) `{name}` 템플릿으로 만들 수 있습니다.
b. 정확히 ( )에 입력한 Veeva 속성 이름이 Veeva에 존재합니다. (예: `name__v`)\
   c. 속성 유형. 다음 중 하나 `Text` 또는 `Multiline Text`.

2. 필수. Veeva의 속성을 AEM에 매핑합니다.
a. 정확히 ( )에 입력한 Veeva 속성 이름이 Veeva에 존재합니다. (예: `name__v`) b. AEM 속성 이름입니다. AEM 속성에서 선택할 수 있습니다. (예: `jcr:title`) c. 속성 유형. 다음 중 하나 `Text` 또는 `Multiline Text`.


#### 자산 탭

에셋을 동기화하는 경우 에셋 탭에 다음을 입력합니다.

![에셋 탭](assets/asset-tab.png)

1. 필수. AEM에서 Veeva로 속성을 매핑합니다.
a. AEM 속성 이름. AEM 속성에서 선택할 수 있습니다. (예: `/jcr:content/metadata/jcr:title`) `{name}` 템플릿으로 만들 수 있습니다.
b. 정확히 ( )에 입력한 Veeva 속성 이름이 Veeva에 존재합니다. (예: `name__v`) c. 속성 유형. 다음 중 하나 `Text` 또는 `Multiline Text`.

2. 필수. Veeva의 속성을 AEM에 매핑합니다.
a. 정확히 ( )에 입력한 Veeva 속성 이름이 Veeva에 존재합니다. (예: `name__v`) b. AEM 속성 이름입니다. AEM 속성에서 선택할 수 있습니다. (예: `/jcr:content/metadata/jcr:title`) c. 속성 유형. 다음 중 하나 `Text` 또는 `Multiline Text`.

### 추가 설정

#### AEM 사용자 생성

PDF/이미지를 생성하는 동안 AEM에서 페이지를 가져오려면 AEM 사용자를 만들어야 합니다. 다음 링크를 따라 사용자에게 읽기 전용 권한을 만들고 부여합니다.

AEM 6.5.5+를 사용하는 경우:

* [AEM에서 사용자 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/setup-organize-users/adding-configuring-users.html?#create-a-user)
* [AEM에서 사용자에게 권한 추가](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?#permissions-in-aem)

AEM Cloud Service을 사용하는 경우:

* [AEM Cloud Service을 사용하여 사용자 관리](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?#accessing)

PDF/이미지로 변환되고 Veeva로 푸시될 컨텐츠에 대한 AEM 서비스 사용자에게 다음 권한이 필요합니다.

* 읽기

>[!IMPORTANT]
>
> 이러한 작업은 각 시스템에 대해 관리자 자격으로 수행해야 합니다.
> 사용자를 만들고 권한을 설정할 때는 조직 보안 표준을 준수해야 합니다.
>

#### 사용자 생성 정보

이 통합을 사용하려면 Veeva Vault에서 사용자를 작성해야 합니다. 사용자를 만들려면 다음 단계를 수행합니다.

1. 관리자 -> 사용자 및 그룹 -> 자격 증명 모음 사용자 -> 만들기 로 이동합니다.

   ![Veeva User 로 이동](assets/veeva-user-navigate.png)

2. 필요한 입력을 입력합니다. 가장 간단한 설정은 `License Type` 끝 `Full User` 및 `Security Profile` 끝 `Vault Owner`. 완료되면 저장합니다.

   ![Veeva 사용자 만들기](assets/veeva-user-create.png)

사용 중인 특정 Veeva 문서 유형에 대해 다음 권한이 필요합니다.

* 문서 만들기/읽기
* 버전 만들기/읽기
* 메타데이터 만들기/업데이트
* 렌디션 만들기/업데이트

>[!IMPORTANT]
>
> 이러한 작업은 각 시스템에 대해 관리자 자격으로 수행해야 합니다.
> 사용자를 만들고 권한을 설정할 때는 조직 보안 표준을 준수해야 합니다.
>
