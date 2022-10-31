# Bid Request

## **BidRequest Top-Level Object**

| Field  | Type                    | Status   | Comment                                                                                                                                                                                                               |
| ------ | ----------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id     | string                  | required | <p>각각의 BidRequest에 대한 유니크한 ID </p><p>(e.g. "23bf9332")</p>                                                                                                                                                            |
| imp    | object Array            | required | <p>'imp' Object</p><p>AX는 다수의 Imp Object를 지원하지 않습니다</p>                                                                                                                                                               |
| site   | object                  | required | <p>'Site' Object</p><p><mark style="color:red;">*웹일 경우 필수</mark></p>                                                                                                                                                  |
| app    | object                  | required | <p>'app' Object</p><p><mark style="color:red;">*웹일 경우 필수</mark></p>                                                                                                                                                   |
| device | object                  | required | 'device' Object                                                                                                                                                                                                       |
| user   | object                  | optional | 'User' Object                                                                                                                                                                                                         |
| at     | <p>Integer<br>기본값 2</p> | optional | 옥션 타입. 1=First Price, 2=Second Price                                                                                                                                                                                  |
| tmax   | intiger                 | optional | 응답 최대 허용 시간(1/1000초 단위)                                                                                                                                                                                               |
| cur    | <p>string<br>array</p>  | optional | <p>허용 가능한 입찰가 통화 단위. ISO-4217 참조.  </p><p>(e.g. "KRW", "USD")</p>                                                                                                                                                     |
| bcat   | <p>string<br>array</p>  | optional | <p>차단 광고주 카테고리 리스트 </p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=39&#x26;zoom=100,92,198">IAB OpenRTB 2.5 표5.1 Content Categories</a> 참조) </p> |
| badv   | <p>string<br>array</p>  | optional | <p>차단 광고주 도메인 리스트 </p><p>(e.g. "google.com","apple.com")</p>                                                                                                                                                          |
| test   | <p>Integer<br>기본값 0</p> | optional | 0=상용 모드, 1=테스트 모드                                                                                                                                                                                                     |
| source | object                  | optional | 'source' Object                                                                                                                                                                                                       |

## **Imp Object**

AX는 다수의 Imp Object를 지원하지 않지만, 다수의 Imp Object를 포함한 BidRequest가 들어올 경우 최상단의 Imp Object에 대해서만 입찰 여부를 판단합니다.

| Field        | Type                            | Status                                      | Comment                                                                   |
| ------------ | ------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------- |
| id           | string                          | required                                    | <p>BidRequest에 포함된 각각의 Impression에 대한 유니크한 ID</p><p>(보통 1부터 시작) </p>      |
| banner       | object                          | required                                    | <p>'banner' object<br><mark style="color:red;">*banner일 경우 필수</mark></p>  |
| native       | object                          | required                                    | <p>'native' object<br><mark style="color:red;">*banner일 경우 필수</mark> </p> |
| tagid        | string                          | <mark style="color:orange;">required</mark> | 광고 지면 및 광고 태그에 대한 ID                                                      |
| bidfloor     | <p>float; <br>기본값 0</p>         | required                                    | 이 Impression에 입찰할 수 있는 최소 CPM                                             |
| bidfloorrate | <p>string;</p><p>기본값 “USD” </p> | optional                                    | <p>Bidfloor에서 지정한 최소 CPM의 통화단위.</p><p>(ISO-4217 참조) </p>                  |
| secure       | <p>Integer<br>기본값 0</p>         | optional                                    | 광고 노출에 HTTPS URL 마크업이 필요한지 여부를 나타내는 플래그. 0=비보안(http), 1=보안(https)         |
| pmp          | object                          | optional                                    | ‘PMP’ Object, 별도 협의된 Private Marketplace Deals에 대한 정보                     |

## Banner Object

| Field | Type                    | Status   | Comment                                                                                                                                                                                                      |
| ----- | ----------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id    | string                  | optional | <p>하나의 ‘Imp’ Object 안에서 ‘Banner’ Object에 할당된 유니크한 ID</p><p>(보통 1부터 시작)</p>                                                                                                                                   |
| w     | Integer                 | required | 배너의 넓                                                                                                                                                                                                        |
| h     | Integer                 | required | 배너의 높이                                                                                                                                                                                                       |
| btype | <p>Integer<br>array</p> | optional | <p>차단 배너 광고 타입 </p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=50&#x26;zoom=100,92,96">IAB OpenRTB 2.5 표5.2 Banner Ad Types</a> 참조)</p> |
| battr | <p>Integer<br>array</p> | optional | 차단 크리에이티브 타입 ([IAB OpenRTB 2.5 표5.3 Creative Attributes](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=50\&zoom=100,92,322) 참조)                        |

## Native Object <a href="#native-object" id="native-object"></a>

IAB OpenRTB Dynamic Native Ads API 1.1 이후 버전에서는 'Native Markup Request Object'가 Root Object임을 명시하고 있으나(IAB OpenRTB Dynamic Native Ads API 1.2 : 4.1 Native Markup Request Object 하단의 Note 참고), AX에서는 매체가 ‘Native Request’에서 'Native'를 Root Node로 사용하는 경우, ‘Native Response’도 동일하게 'Native'를 Root Node로 응답합니다.

| Field   | Type                    | Status   | comment                                                                                                                                                                               |
| ------- | ----------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| request | string                  | required | IAB Native Ads 스펙의 JSON string AX의 Native 광고 응답은 해당 값의 Root Node를 따름                                                                                                                  |
| ver     | string                  | optional | 사용하는 IAB Native Ads 스펙 버전                                                                                                                                                             |
| api     | <p>Integer<br>array</p> | optional | 지원하는 API framework 리스트                                                                                                                                                                |
| battr   | <p>Integer<br>array</p> | optional | 차단 크리에이티브 타입 ([IAB OpenRTB 2.5 표5.3 Creative Attributes](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=50\&zoom=100,92,322) 참조) |

## PMP Object

| Field            | Type                    | Status   | Comment                                |
| ---------------- | ----------------------- | -------- | -------------------------------------- |
| private\_auction | <p>Integer<br>기본값 0</p> | optional | 0=모든 입찰 허용, 1=지정된 Deal 및 해당 조건으로 입찰 제한 |
| deals            | object array            | optional | 'Deal' Object                          |

## Deal Object

|             |                            |          |                                                                                                      |
| ----------- | -------------------------- | -------- | ---------------------------------------------------------------------------------------------------- |
| id          | string                     | required | 각 Deal에 대한 ID. 사전에 협의된 ID만 사용                                                                        |
| bidfloor    | <p>float;<br>default 0</p> | optional | 이 Impression에 입찰할 수 있는 최소 CPM.                                                                       |
| bidfloorcur | <p>string;<br>기본 "USD"</p> | optional | <p>Bidfloor에서 지정한 최소 CPM의 통화단위.</p><p>(ISO-4217 참조)</p>                                              |
| at          | integer                    | optional | <p>미리 계약한 설정에 따라서 적용. </p><p>1=First Price, 2=Second Price, 3=Fixed Price(Bidfloor의 CPM으로 단가 고정)</p> |
| wseat       | string array               | optional | 이 Deal에 입찰할 수 있는 Seat ID리스트                                                                          |
| wadomain    | string array               | optional | 이 Deal에 입찰할 수 있는 광고주 도메인 리스                                                                          |
| ext         | object                     | optional | Deal Object – Extension                                                                              |

### Deal Object -Extension

| Field | Type    | Status   | Comment                                                   |
| ----- | ------- | -------- | --------------------------------------------------------- |
| type  | integer | optional | 1=Deal type이 Preferred Deal, 2=Deal type이 Private Auction |

## Device Object

| Field      | Type    | Status   | Comment                                                                                                                                                                                     |
| ---------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ua         | string  | required | 브라우저 유저 에이전트                                                                                                                                                                                |
| dnt        | integer | optional | <p>광고 추적 제한(Do Not Track)</p><p>0 = 추적 허용, 1 = 추적 금지 </p>                                                                                                                                   |
| ip         | string  | required | 디바이스의 IP                                                                                                                                                                                    |
| devicetype | integer | optional | <p>디바이스의 종류 </p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=56&#x26;zoom=100,92,408">IAB OpenRTB 2.5 표5.21</a> 참조)</p> |
| make       | string  | optional | 디바이스 제조사 (e.g. "Apple")                                                                                                                                                                     |
| model      | string  | optional | 디바이스 모델 (e.g. "iPhone")                                                                                                                                                                     |
| os         | string  | optional | 디바이스 OS (e.g. "iOS")                                                                                                                                                                        |
| osv        | string  | optional | 디바이스 OS의 버전 (e.g. "9.0")                                                                                                                                                                    |
| geo        | object  | optional | 디바이스의 위치 정보를 나타내는 'Geo'Object                                                                                                                                                               |
| ifa        | string  | optional | IDFA 또는 GAID와 같은 값의 광고 트래킹을 위한 유저 ID                                                                                                                                                        |
| didsha1    | string  | optional | <p>SHA1으로 해싱된 하드웨어 디바이스 ID </p><p>(e.g. IMEI)</p>                                                                                                                                           |
| didmd5     | string  | optional | <p>MD5 으로 해싱된 하드웨어 디바이스 ID </p><p>(e.g. IMEI)</p>                                                                                                                                           |
| dpidsha1   | string  | optional | <p>SHA1으로 해싱된 플랫폼 디바이스 ID </p><p>(e.g. Android ID)</p>                                                                                                                                      |
| dpidmd5    | string  | optional | <p>MD5으로 해싱된 플랫폼 디바이스 ID </p><p>(e.g. Android ID)</p>                                                                                                                                       |

## Geo Object

| Field   | Type    | Status   | Comment                                                                                                                                                                                                   |
| ------- | ------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| lat     | float   | optional | 지리상의 위도                                                                                                                                                                                                   |
| lon     | float   | optional | 지리상의 경도                                                                                                                                                                                                   |
| type    | integer | optional | <p>위치 정보 방식 </p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=56&#x26;zoom=100,92,206">IAB OpenRTB 2.5 표5.20 Location Type</a> 참조)</p> |
| country | string  | optional | ISO-3166-1-alpha-3을 사용하는 국가 코드                                                                                                                                                                            |
| region  | string  | optional | ISO-3166-2을 사용하는 지역 코드                                                                                                                                                                                    |

## Site Object

| Field     | Type         | Status   | Comment                                                                                                                                                                                                                  |
| --------- | ------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id        | string       | optional | 사이트 ID                                                                                                                                                                                                                   |
| name      | string       | optional | 사이트 이름                                                                                                                                                                                                                   |
| domain    | string       | optional | 매체 도메인 (e.g. "news.nhnace.com")                                                                                                                                                                                          |
| cat       | string array | optional | <p>사이트에 대한 컨텐츠 카테고리 리스트</p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=39&#x26;zoom=100,92,198">IAB OpenRTB 2.5 표5.1 Content Categories</a> 참조)</p> |
| page      | string       | required | 현재 페이지의 URL                                                                                                                                                                                                              |
| ref       | string       | optional | 현재 페이지로 이동 한 Referrer URL                                                                                                                                                                                                |
| mobile    | integer      | optional | 모바일 디바이스 최적화 레이아웃 제공 여부 0=아니오, 1=예                                                                                                                                                                                       |
| publisher | object       | optional | 'Publisher' Object                                                                                                                                                                                                       |

## App Object

| Field     | Type         | Status   | Comment                                                                                                                                                                                    |
| --------- | ------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id        | string       | optional | 앱 ID                                                                                                                                                                                       |
| name      | string       | optional | 앱 이름                                                                                                                                                                                       |
| bundle    | string       | required | <p>앱 번들 또는 패키지 </p><p>(e.g. "com.nhnent.friendspop")</p>                                                                                                                                   |
| domain    | string       | optional | 앱의 도메인                                                                                                                                                                                     |
| cat       | string array | optional | 앱에 대한 컨텐츠 카테고리 리스트 ([IAB OpenRTB 2.5 표5.1 Content Categories](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=39\&zoom=100,92,198) 참조) |
| storeurl  | string       | optional | 앱의 스토어 URL                                                                                                                                                                                 |
| publisher | object       | optional | 'Publisher' Object                                                                                                                                                                         |

## Publisher Object

| Field | Type   | Status   | Comment |
| ----- | ------ | -------- | ------- |
| id    | string | required | 매체 ID   |

## User Object

| Field    | Type   | Status   | Comment                                                                      |
| -------- | ------ | -------- | ---------------------------------------------------------------------------- |
| id       | string | optional | 매체의 유저 ID                                                                    |
| buyeruid | string | optional | <p>매체의 유저 ID와 매핑 된AX의 유저 ID.</p><p>이 정보를 제공받기 위해 Cookie Sync 과정이 필요합니다. </p> |

## Source Object

| Field | Type   | Status   | Comment                                                                                                        |
| ----- | ------ | -------- | -------------------------------------------------------------------------------------------------------------- |
| tid   | string | optional | <p>이 BidRequest에 입찰하는 모든 파트너들이 공통으로 획득할 수 있는 Transaction ID</p><p>Multiple Exchanges 하에서 하나의 요청임을 식별할 때 사용</p> |
| ext   | string | optional | Source Object - Extension                                                                                      |

### Source Object - Extension

| Field  | Type   | Status   | Comment              |
| ------ | ------ | -------- | -------------------- |
| schain | object | optional | 'SupplyChain' Object |

### SupplyChain Object

| Field    | Type         | Status   | Comment                                                                             |
| -------- | ------------ | -------- | ----------------------------------------------------------------------------------- |
| complete | integer      | required | 사이트, 앱 또는 다른 인벤토리의 매체 소유자로 돌아가는 트랜젝션에 관련된 모든 노드가 포함되어 있는지 여부를 나타내는 플래그 (0=아니오, 1=예) |
| nodes    | object array | required | 체인 순서에 따른 'SupplyChainNode' Object                                                  |
| ver      | string       | required | SupplyChain 버전                                                                      |

### SupplyChainNode Object

| Field  | Type    | Status    | Comment                                                                                    |
| ------ | ------- | --------- | ------------------------------------------------------------------------------------------ |
| ais    | string  | required  | 입찰자가 연결하는 SSP, Exchange, Header Wrapper 등 시스템의 표준 도메인으로 ads.txt 파일에서 판매자가 식별하는데 사용하는 값과 동일 |
| sid    | string  | required  | 광고 시스템 내의 판매자 또는 리셀러 계정과 관련된 식별자                                                           |
| rid    | string  | requiredv | 판매자가 발행 한 요청의 OpenRTB RequestId                                                            |
| name   | string  | optional  | 지정된 seller\_id에 따라 거래되는 인벤토리에 대해 지급되는 회사(법적 실체)의 이름                                        |
| domain | string  | optional  | 이 노드로 표시되는 엔티티의 비즈니스 도메인 이름                                                                |
| hp     | integer | required  | 인벤토리 지불 흐름에 관여할 것인지 여부 표시 Supply Chain 1.0버전에서 hp값은 1                                      |

