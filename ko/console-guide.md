## Content Delivery > CDN > 콘솔 사용 가이드

여기에서는 콘솔에서 CDN 서비스를 구성하고 이용하는 방법을 설명합니다.

## CDN 서비스 생성 순서

**Contents Delivery > CDN**의 **CDN 서비스** 탭에서 **생성** 버튼을 클릭하면 **CDN 서비스 생성** 창이 나타납니다.
CDN 서비스에 이용할 도메인 이름은 자동으로 생성됩니다. 소유하고 있는 도메인이 있다면, 도메인 별칭(Domain Alias) 기능을 이용해 서비스할 수 있습니다.

### CDN 서비스

![cdn_01_201812](https://static.toastoven.net/prod_cdn/cdn_01_201812.png)

- **서비스 지역**
  서비스할 지역을 선택합니다.
  서비스 제공 형태에 따라 KOREA 또는 GLOBAL을 선택할 수 있습니다. 각국에 존재하는 캐시 서버를 이용해 전 세계를 대상으로 서비스하려면 GLOBAL을 선택하고, 한국 내에서만 서비스하려면 KOREA를 선택합니다. KOREA를 선택하면 좀 더 낮은 가격에 서비스를 이용할 수 있습니다.

- **설명**
  CDN 서비스에 추가 설명을 입력합니다.

- **원본 서버**
  TOAST에서 만든 인스턴스나 기존에 보유하고 있는 서버를 이용해 서비스할 수 있습니다. 원본 서버는 IP 또는 도메인 형태로 입력할 수 있으며, 포트를 지정할 수 있습니다.
- **원본 경로**
  URL 경로 형태의 하위 경로는 '/'를 포함하여 원본 경로에 입력해 주세요. **원본 경로**는 선택 항목입니다.

- **도메인 별칭**
  도메인 별칭을 설정합니다.
  CDN 서비스 생성이 완료되면 *.cdn.toastcloud.com 형태의 서비스 도메인이 자동으로 발급되며, 발급된 도메인을 그대로 서비스에 이용할 수 있습니다.
  하지만 개인 또는 회사가 소유한 도메인을 이용해 CDN 서비스를 제공해야 할 때는, **도메인 별칭** 설정을 이용할 수 있습니다.
  **도메인 별칭**를 이용하면 TOAST에서 제공하는 도메인 외에 개인 혹은 회사가 소유한 도메인으로도 CDN 서비스를 사용할 수 있습니다.
  **도메인 별칭**에 소유한 도메인 주소를 입력하고, 해당 도메인의 네임 서버 설정을 변경해 주세요.
  TOAST에서 발급받은 CDN 서비스 주소를 CNAME 레코드로 추가하면 소유한 도메인으로도 서비스할 수 있습니다.

> [주의]
> CDN 서비스가 생성되면 `*.cdn.toastcloud.com` 서비스 도메인이 발급됩니다.
> 생성된 CDN 서비스 도메인은 **http** 프로토콜만 지원됩니다. **https** 프로토콜의 서비스 도메인 지원이 필요한 경우 고객센터를 통해 문의해주세요.
> `*.cdn.toastcloud.com` 서비스 도메인을 통해 리소스에 접근할 수 없을 때는 아래의 내용을 확인해 주세요.
> 
>
> 1. CDN 서비스 상태가 '녹색'(서비스 중) 상태가 되었는지 확인해 주세요.
> 2. 원본 서버(origin server)에서 특정 호스트의 접근만 허용하고 있는지 확인해 주세요.
> 3. 사용자가 CDN 서비스 도메인에서 리소스를 요청하면 `Host` 요청 헤더는 사용자가 요청한 주소인 `*.cdn.toastcloud.com`으로 설정되어 원본 서버에 요청합니다.
> 따라서, 원본 서버에서 `*.cdn.toastcloud.com` 호스트에 대한 접근이 허용되지 않은 경우 CDN 캐시 서버는 원본 서버로부터 리소스를 가져올 수 없습니다.
> 이 경우 원본 서버의 Virtual host 설정에 `*.cdn.toastcloud.com` 호스트를 등록해야 합니다.


> [주의]
> 도메인 별칭을 등록한 경우 기본으로 제공된 CDN 서비스 도메인 `*.cdn.toastcloud.com`은 퍼지 작업이 되지 않습니다. 
> 등록한 도메인 별칭 주소에 대해서만 퍼지 작업이 진행되므로 주의해주세요.

* 도메인 별칭 사용 예

CDN 서비스를 생성한 후 random-exam.cdn.toastcloud.com이라는 도메인이 발급되고, 기존 고객이 소유하던 alias.nhnentcustomer.com을 이용하여 서비스하기 위한 설정 방법입니다.

    1. TOAST CDN 생성 이후 자동으로 발급된 random-exam.cdn.toastcloud.com을 확인합니다.
    2. 기본정보 설정 탭의 Domain Alias 항목에 서비스에 사용할 고객 도메인 alias.nhnentcustomer.com을 입력합니다.
    3. nhnentcustomer.com 네임서버 관리 항목에서 random-exam.cdn.toastcloud.com을 이용해 CNAME 레코드를 추가합니다. (도메인 제공 업체에 따라 설정 방법은 다를 수 있습니다. 자세한 사항은 도메인 제공 업체에게 문의해주십시오.)
    4. alias.nhnentcustomer.com으로 서비스를 시작합니다.

### 캐시

캐시 아래에서 캐시 만료를 설정할 수 있습니다.
![cdn_02_201812](https://static.toastoven.net/prod_cdn/cdn_02_201812.png)

- **캐시 만료 설정**
원하는 캐시 만료 시간을 지정할 수 있습니다. **원본 설정 사용** 옵션이 기본값입니다.
  
  * 원본 설정 사용: 원본 서버의 캐시 만료 설정을 이용하도록 설정합니다.
  * 사용자 설정 사용: 원하는 캐시 만료 시간을 설정할 수 있습니다.

- **캐시 만료 시간(초)**
캐시 만료 시간을 지정하려면 **사용자 설정 사용** 버튼을 클릭하고 **캐시 만료 시간(초)**에서 캐시 만료 시간을 변경합니다.

> [주의]
> 만일 원본 서버 설정에 캐시 만료 시간이 지정되어 있다면 콘솔에서 설정한 **캐시 만료 시간 (초)**값은 무시됩니다.
> CDN 서비스를 이용해 만료 시간을 지정하고 싶다면 원본 서버의 캐시 만료 설정을 제거합니다.
>
> [참고]
> 캐시 만료 시간 기본값은 0입니다. 기본값을 0으로 설정하면 캐시 만료 시간은 604,800(단위/초)입니다.
> 캐시 만료 시간은 기본값인 0부터 2,147,483,647(단위/초)까지 입력할 수 있습니다.

- **리퍼러(referrer) 헤더 접근 관리**
  리퍼러 접근 관리를 설정합니다.
  웹 페이지에서 사용자 콘텐츠를 링크하여 리소스를 요청하는 경우 리퍼러 헤더에 링크한 URL의 경로가 전달되어 어떤 경로에서 요청이 유입된건지 알 수 있습니다.
  리퍼러 접근 관리는 리퍼러 헤더를 참고하여 특정 리퍼러만 사용자 콘텐츠에 접근할 수 있도록 설정할 수 있습니다.
  리퍼러는 정규 표현식 형태로 입력할 수 있으며, 여러 개의 리퍼러를 제어할 경우 입력 창에 라인을 추가하여 입력합니다.

  * Blacklist(블랙 리스트) 타입:
      * 특정 리퍼러에서의 접근을 제한할 때 적합합니다.
      * 요청 헤더의 리퍼러값이, 설정한 정규 표현식에 매칭되는 문자열이면 콘텐츠 접근이 제한됩니다. 매칭되지 않는 문자열이면 콘텐츠 접근이 허용됩니다.
  * Whitelist(화이트 리스트) 타입:
      * 특정 리퍼러에서만 접근을 허용할 때 적합합니다.
      * 요청 헤더의 리퍼러값이 정규 표현식에 매칭되는 문자열이면 콘텐츠 접근이 허용됩니다. 매칭되지 않는 문자열이면 콘텐츠 접근이 제한됩니다.

> [주의]
> 요청 헤더에 리퍼러가 없을 때는 리퍼러 설정의 접근 제어가 동작하지 않습니다.
>
> [예시]
> * 타입: Whitelist
> * 정규 표현식: `^https://[a-zA-Z0-9._-]*\.toast\.com/.*`
> 임의의 toast.com 서브 도메인의 하위 경로에서 리소스를 요청한 경우에만 콘텐츠 접근을 허용하게 됩니다.
>
> [참고]
> 일부 문자는 정규 표현식에서 특수 문자로 사용됩니다. 
> 점(`.`)을 예로 들자면, 정규 표현식에서 점(`.`)은 모든 문자와 일치함을 나타내는 특수 문자입니다. 
> 특수 문자로의 의미가 아닌 일반 문자 그대로 해석이 필요하다면 이스케이프 문자 백슬래시(`\`)를 특수 문자 앞에 추가하세요. (예: `\.`)
> 정규 표현식의 특수 문자는 `^ . [ ] $ ( ) | * + ? { } \` 등이 있습니다.
> 여러 개의 리퍼러를 제어할 경우 다음 라인에 연속하여 입력합니다.
> API를 통해 여러 개의 리퍼러를 설정할 때는 \n 토큰으로 구분해 입력합니다.


### 콜백

CDN 서비스 변경 작업(생성, 수정, 정지/재개, 삭제 작업)은 변경 요청 후 최대 수십 분이 필요할 수 있습니다. 
서비스 변경 작업이 완료된 후 미리 설정한 콜백 URL로 서비스 변경 작업의 완료 여부와 서비스 정보를 전달받을 수 있습니다.

![cdn_03_201812](https://static.toastoven.net/prod_cdn/cdn_03_201812.png)


1. **HTTP Method**와 **콜백 URL**을 입력합니다.
2. Request URI의 Query Parameter로 CDN 서비스 변경 작업에 대한 결과를 받으려면 **콜백 URL**에 Path 변수를 포함해 입력해 주세요.

| Path Variable | 설명 | 예시 전달 값 |
| ------------- | --- | ------- |
| {appKey} | CDN 서비스 앱 키 | 콘솔에서 발급받은 앱 키 |
| {domain} | CDN 서비스 이름 | xxxxxx.cdn.toastcloud.com |
| {status} | 현재 CDN 서비스 상태 | OPEN, SUSPEND, CLOSE, ERROR |
| {isSuccessful} | 서비스 변경 작업 성공 여부(API V1.0은 지원하지 않습니다.) | "true" 또는 "false" |
3. **확인** 버튼을 클릭하면 CDN 서비스 생성 요청이 완료됩니다.

> 예시
> GET http://test.callback.com?appKey={appKey}&domain={domain}&status={status}&deploySuccess={isSuccessful}
- 콜백 전달 시 CDN 서비스의 정보를 요청 본문(Request Body)으로 전달합니다.
- API V1.0으로 변경할 경우 요청 본문의 내용은 아래와 같습니다.
```
    {
      "seq": Integer,
      "appKey": String,
      "domain": String,
      "domainAlias": String,
      "type": String,
      "region": String,
      "description": String,
      "status": String, 
      "createTime": DateTime,
      "useOrigin": String,
      "maxAge": String,
      "referrerType": String,
      "referrers": String,
      "deleteTime": DateTime,
      "company": String,
      "origins":[
      {
         "seq": Integer,
         "distributionSeq": Integer,
         "origin": String,
         "originPath": String,
         "port":Integer,
      }
      ],
      "callbackHttpMethod": String,
      "callbackUrl": String
}
```
* CDN 콘솔에서 변경하거나 API V1.5로 변경할 경우 응답 형식은 아래와 같습니다.
```
    {
      "header":{
      "resultCode": Integer,
      "resultMessage": String,
      "isSuccessful": Boolean
      },
      "distribution":{
      "seq": String,
      "appKey": String,
      "domain": String,
      "domainAlias": String,
      "type": String,
      "region": String,
      "description": String,
      "status": String,
      "createTime": DateTime,
      "useOrigin": String,
      "maxAge": String, 
      "referrerType": String,
      "referrers": String,
      "deleteTime": DateTime,
      "company": String,
      "origins":[
         {
            "seq": Integer,
            "distributionSeq": Integer,
            "origin": String,
            "originPath": String,
            "port": Integer
         }
      ],
      "callback":{
         "httpMethod": String,
         "url": String
      }
      },
      "successful": Boolean
}
```
> [주의]
> API V1.0과 V1.5 버전에 따라 콜백 동작이 다르므로 유의해 주세요.
> API V1.0은 CDN 서비스 생성과 수정 시에만 콜백이 호출되고, API V1.5는 생성,수정,일시 정지와 재개,삭제 시 콜백을 호출합니다.
> API 버전에 따라 콜백 요청 본문(Request Body)의 JSON 데이터 형식이 다르므로 유의해 주세요.


**생성을 요청한 후 서비스 배포가 완료될 때까지 몇 분 정도(최대 한 시간) 필요합니다. 배포가 완료된 후 서비스를 이용할 수 있습니다.**

## 설정

### CDN 서비스 설정 변경

추가 설명 및 원본 서버 정보를 변경할 수 있습니다.
하지만 서비스 이름과 지역은 변경할 수 없으므로 변경을 원한다면 기존 서비스를 삭제한 후 새로운 서비스로 생성해야 합니다.

1. 변경을 원하는 서비스를 CDN 서비스 목록에서 선택합니다.
2. 화면 아래 **기본 정보** 탭의 **수정** 버튼을 클릭합니다.

다음과 같이 변경할 수 있는 항목이 활성화됩니다.

![cdn_04_201812](https://static.toastoven.net/prod_cdn/cdn_04_201812.png)

* 변경할 수 있는 항목은 설명, 원본 서버 정보, 도메인 별칭, 콜백입니다.
* **확인** 버튼을 클릭해 변경을 완료합니다.

**원본 서버가 변경되면 기존에 캐시되어 있던 모든 내용이 재배포되며 콘텐츠양에 따라 재배포 시간은 달라집니다.**

### CDN 캐시 설정 변경

1. 변경을 원하는 서비스를 CDN 서비스 목록에서 선택합니다.
2. **캐시 설정** 탭의 **수정** 버튼을 클릭합니다.

다음과 같이 변경할 수 있는 항목이 활성화됩니다.

![cdn_05_201812](https://static.toastoven.net/prod_cdn/cdn_05_201812.png)

* 변경할 수 있는 항목은 캐시 만료 설정, 캐시 만료 시간, 리퍼러 헤더 접근 관리, 콜백입니다.
* **확인** 버튼을 클릭해 변경을 완료합니다.

### CDN 캐시 재배포

원본 콘텐츠의 내용이 변경된 경우 기존에 지정된 캐시 만료 시간 이후에는 새로운 콘텐츠로 캐시가 업데이트됩니다. 하지만 빠르게 캐시 내용을 재배포하고 싶은 경우 **캐시 재배포** 기능을 이용해 기존 캐시를 새로운 콘텐츠로 업데이트합니다.

1. 변경을 원하는 서비스를 CDN 서비스 목록에서 선택합니다.
2. **캐시 재배포** 탭을 클릭합니다.
![cdn_06_201812](https://static.toastoven.net/prod_cdn/cdn_06_201812.png)
3. 캐시 재배포 타입을 선택합니다. 3가지 타입 중에 선택할 수 있습니다.
  * 특정 파일: 정확한 파일 이름과 경로를 설정해 원하는 파일만 재배포할 수 있습니다.
      * 예) /path/to/file1.jpg
  * 와일드카드: 파일 이름과 경로 이름에 와일드카드 문자를 이용할 수 있습니다.
      * \*: 임의의 문자열
      * ?: 1개의 문자
      * \: Escape 문자
          * 예) /images/games/\*.jpg
          * /\_/sports/\_.jpg
          * /images/sports/ac?e/\*.jpg
  * 전체 파일: 모든 캐시를 한꺼번에 재배포합니다.
4. 선택한 캐시 재배포 타입에 맞게 재배포할 파일을 지정합니다.
5. **캐시 재배포** 버튼을 클릭해 재배포를 요청합니다.

재배포까지는 몇 분 정도 필요합니다. 용량에 따라 필요한 시간이 달라질 수 있습니다.

> [주의] 캐시 재배포 사용량 제한
> 서비스별로 캐시 재배포 사용 횟수가 제한되므로 제한 사용량을 초과하면 사용량이 초기화된 이후에 다시 사용할 수 있습니다.
> 
> 
> * 특정 파일 타입: 시간당 60회 제한, 한 번에 요청할 수 있는 최대 Path 수는 1000개
> * 와일드카드 타입: 시간당 60회 제한, 한 번에 요청할 수 있는 최대 Path 수는 10개
> * 전체 파일 타입: 시간당 5회 제한


> [주의] 복수 개의 도메인 별칭을 사용 중인 CDN 서비스의 캐시 재배포 
> 복수 개의 도메인 별칭이 등록된 CDN 서비스는 요청한 퍼지 경로에 대해 각 도메인 별칭 별로 퍼지작업이 진행됩니다. 
> 
> (예시)
> `custom1.domain-alias.com` 과 `custom2.domain-alias.com` 이 도메인 별칭으로 설정된 CDN 서비스가 있다고 가정합니다.
> 위 CDN 서비스에 대해 **특정 파일** 타입으로 퍼지 경로 `/images/photo.png` 로 퍼지를 요청 한 경우 아래 2개의 퍼지 경로로 퍼지가 수행됩니다. 
>
> - custom1.domain-alias.com/images/photo.png
> - custom2.domain-alias.com/images/photo.png 
>
> (등록된 도메인 별칭 수 X 요청한 퍼지 경로 수) 만큼 퍼지 경로가 추가되어 퍼지가 진행되므로 유의해주세요. 
> 만일, 전체 퍼지 경로 수가 퍼지 사용량 제한의 요청 당 최대 퍼지 경로 수를 초과한 경우에는 요청 당 최대 퍼지 경로 수만큼씩 나누어 요청이 됩니다. 
> 나누어 진행된 퍼지 요청 수 만큼 퍼지 사용량 제한 사용량은 증가하므로 퍼지 사용량 초과에 유의해주세요.


### CDN 감시 설정

예상치 못한 트래픽이 발생할 때를 대비해 감시 설정을 등록할 수 있습니다. 지정한 값 이상의 트래픽이 발생하면 이메일을 발송하며, 강제 정지 옵션을 설정하면 이메일을 발송한 후 CDN 서비스를 정지합니다.

1. 변경을 원하는 서비스를 CDN 서비스 목록에서 선택합니다.
2. **감시 설정** 탭의 **수정** 버튼을 클릭합니다.
![cdn_07_201812](https://static.toastoven.net/prod_cdn/cdn_07_201812.png)
  * 누적 트래픽 타입으로 제한할 트래픽양을 지정합니다. 단위는 바이트입니다.
  * +/- 버튼을 클릭해 여러 개의 감시 설정을 추가하거나 삭제합니다.
  * 지정한 값 이상의 트래픽이 감지되었을 때 서비스 강제 정지를 원하면 강제 정지 설정을 **예**로 활성화합니다.
3. **확인** 버튼을 클릭해 변경된 내용을 적용합니다.

## 통계

네트워크 전송량, HTTP 상태 코드별 통계 및 다운로드가 가장 많은 콘텐츠의 순위 통계를 확인할 수 있습니다.
1. **Contents Delivery > CDN**의 **통계** 탭을 클릭합니다.
![cdn_08_201812](https://static.toastoven.net/prod_cdn/cdn_08_201812.png)
2. 통계를 확인하려면 CDN 서비스를 선택합니다.
3. 검색 기간을 입력합니다.
4. 검색 기간 내 데이터 주기는 선택한 기간에 따라 자동으로 선택됩니다.
5. **검색** 버튼을 클릭합니다.