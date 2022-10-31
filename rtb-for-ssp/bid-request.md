# Bid Request

## **BidRequest Top-Level Object**

| Field  | Type                    | Status   | Comment                                                                     |
| ------ | ----------------------- | -------- | --------------------------------------------------------------------------- |
| id     | string                  | required | <p>각각의 BidRequest에 대한 유니크한 ID </p><p>(e.g. "23bf9332")</p>                  |
| imp    | object Array            | required | <p>'imp' Object</p><p>AX는 다수의 Imp Object를 지원하지 않습니다</p>                     |
| site   | object                  | required | <p>'Site' Object</p><p><mark style="color:red;">*웹일 경우 필수</mark></p>        |
| app    | object                  | required | <p>'app' Object</p><p><mark style="color:red;">*웹일 경우 필수</mark></p>         |
| device | object                  | required | 'device' Object                                                             |
| user   | object                  | optional | 'User' Object                                                               |
| at     | <p>Integer<br>기본값 2</p> | optional | 옥션 타입. 1=First Price, 2=Second Price                                        |
| tmax   | intiger                 | optional | 응답 최대 허용 시간(1/1000초 단위)                                                     |
| cur    | <p>string<br>array</p>  | optional | <p>허용 가능한 입찰가 통화 단위. ISO-4217 참조.  </p><p>(e.g. "KRW", "USD")</p>           |
| bcat   | <p>string<br>array</p>  | optional | <p>차단 광고주 카테고리 리스트 </p><p>(IAB OpenRTB 2.5 표5.1 Content Categories 참조) </p> |
| badv   | <p>string<br>array</p>  | optional | <p>차단 광고주 도메인 리스트 </p><p>(e.g. "google.com","apple.com")</p>                |
| test   | <p>Integer<br>기본값 0</p> | optional | 0=상용 모드, 1=테스트 모드                                                           |
| source | object                  | optional | 'source' Object                                                             |

## **Imp Object**

AX는 다수의 Imp Object를 지원하지 않지만, 다수의 Imp Object를 포함한 BidRequest가 들어올 경우 최상단의 Imp Object에 대해서만 입찰 여부를 판단합니다.

| Field        | Type                            | Status                                      | Comment                                                                 |
| ------------ | ------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------- |
| id           | string                          | required                                    | <p>BidRequest에 포함된 각각의 Impression에 대한 유니크한 ID</p><p>(보통 1부터 시작) </p>    |
| banner       | object                          | required                                    | <p>'banner' object<br><mark style="color:red;">*banner일 경우 필</mark></p> |
| native       | object                          | required                                    | <p>'native' object<br><mark style="color:red;">*banner일 경우 필</mark></p> |
| tagid        | string                          | <mark style="color:orange;">required</mark> | 광고 지면 및 광고 태그에 대한 ID                                                    |
| bidfloor     | <p>float; <br>기본값 0</p>         | required                                    | 이 Impression에 입찰할 수 있는 최소 CPM                                           |
| bidfloorrate | <p>string;</p><p>기본값 “USD” </p> | optional                                    | <p>Bidfloor에서 지정한 최소 CPM의 통화단위.</p><p>(ISO-4217 참조) </p>                |
| secure       | <p>Integer<br>기본값 0</p>         | optional                                    | 광고 노출에 HTTPS URL 마크업이 필요한지 여부를 나타내는 플래그. 0=비보안(http), 1=보안(https)       |
| pmp          | object                          | optional                                    | ‘PMP’ Object, 별도 협의된 Private Marketplace Deals에 대한 정보                   |

## Banner Object

| Field | Type                    | Status   | Comment                                                                    |
| ----- | ----------------------- | -------- | -------------------------------------------------------------------------- |
| id    | string                  | optional | <p>하나의 ‘Imp’ Object 안에서 ‘Banner’ Object에 할당된 유니크한 ID</p><p>(보통 1부터 시작)</p> |
| w     | Integer                 | required | 배너의 넓                                                                      |
| h     | Integer                 | required | 배너의 높이                                                                     |
| btype | <p>Integer<br>array</p> | optional | 차단 배너 광고 타입 (IAB OpenRTB 2.5 표5.2 Banner Ad Types 참조)                      |
| battr | <p>Integer<br>array</p> | optional | 차단 크리에이티브 타입 (IAB OpenRTB 2.5 표5.3 Creative Attributes 참조)                 |

## Native Object <a href="#native-object" id="native-object"></a>

IAB OpenRTB Dynamic Native Ads API 1.1 이후 버전에서는 'Native Markup Request Object'가 Root Object임을 명시하고 있으나(IAB OpenRTB Dynamic Native Ads API 1.2 : 4.1 Native Markup Request Object 하단의 Note 참고), AX에서는 매체가 ‘Native Request’에서 'Native'를 Root Node로 사용하는 경우, ‘Native Response’도 동일하게 'Native'를 Root Node로 응답합니다.

| Field   | Type                    | Status   | comment                                                              |
| ------- | ----------------------- | -------- | -------------------------------------------------------------------- |
| request | string                  | required | IAB Native Ads 스펙의 JSON string AX의 Native 광고 응답은 해당 값의 Root Node를 따름 |
| ver     | string                  | optional | 사용하는 IAB Native Ads 스펙 버전                                            |
| api     | <p>Integer<br>array</p> | optional | 지원하는 API framework 리스트                                               |
| battr   | <p>Integer<br>array</p> | optional | 차단 크리에이티브 타입 (IAB OpenRTB 2.5 표5.3 Creative Attributes 참조)           |

## PMP Object

| Field            | Type                    | Status   | Comment                                |
| ---------------- | ----------------------- | -------- | -------------------------------------- |
| private\_auction | <p>Integer<br>기본값 0</p> | optional | 0=모든 입찰 허용, 1=지정된 Deal 및 해당 조건으로 입찰 제한 |
| deals            | object array            | optional | 'Deal' Object                          |

## Deal Object

|             |                            |          |                                                                                        |
| ----------- | -------------------------- | -------- | -------------------------------------------------------------------------------------- |
| id          | string                     | required | 각 Deal에 대한 ID. 사전에 협의된 ID만 사용                                                          |
| bidfloor    | <p>float;<br>default 0</p> | optional | 이 Impression에 입찰할 수 있는 최소 CPM.                                                         |
| bidfloorcur | <p>string;<br>기본 "USD"</p> | optional | <p>Bidfloor에서 지정한 최소 CPM의 통화단위.</p><p>(ISO-4217 참조)</p>                                |
| at          | integer                    | optional | 미리 계약한 설정에 따라서 적용. 1=First Price, 2=Second Price, 3=Fixed Price(Bidfloor의 CPM으로 단가 고정) |
| wseat       | string array               | optional | 이 Deal에 입찰할 수 있는 Seat ID리스트                                                            |
| wadomain    | string array               | optional | 이 Deal에 입찰할 수 있는 광고주 도메인 리스                                                            |
| ext         | object                     | optional | Deal Object – Extension                                                                |

## Deal Object -Extension

| Field | Type    | Status   | Comment                                                   |
| ----- | ------- | -------- | --------------------------------------------------------- |
| type  | integer | optional | 1=Deal type이 Preferred Deal, 2=Deal type이 Private Auction |

## Device Object

| Field      | Type    | Status   | Comment                                                   |
| ---------- | ------- | -------- | --------------------------------------------------------- |
| ua         | string  | required | 브라우저 유저 에이전트                                              |
| dnt        | integer | optional | <p>광고 추적 제한(Do Not Track)</p><p>0 = 추적 허용, 1 = 추적 금지 </p> |
| ip         | string  | required | 디바이스의 IP                                                  |
| devicetype | integer | optional | 디바이스의 종류 (IAB OpenRTB 2.5 표5.21 참조)                       |
| make       | string  | optional | 디바이스 제조사 (e.g. "Apple")                                   |
| model      | string  | optional | 디바이스 모델 (e.g. "iPhone")                                   |
| os         | string  | optional | 디바이스 OS (e.g. "iOS")                                      |
| osv        | string  | optional | 디바이스 OS의 버전 (e.g. "9.0")                                  |
| geo        | string  | optional | 디바이스의 위치 정보를 나타내는 'Geo'Object                             |
| ifa        | string  | optional | IDFA 또는 GAID와 같은 값의 광고 트래킹을 위한 유저 ID                      |
| didsha1    | string  | optional | SHA1으로 해싱된 하드웨어 디바이스 ID (e.g. IMEI)                       |
| didmd5     | string  | optional | MD5 으로 해싱된 하드웨어 디바이스 ID (e.g. IMEI)                       |
| dpidsha1   | string  | optional | SHA1으로 해싱된 플랫폼 디바이스 ID (e.g. Android ID)                  |
| dpidmd5    | string  | optional | MD5으로 해싱된 플랫폼 디바이스 ID (e.g. Android ID)                   |

#### Geo Object

| Field | Type | Status | Comment |
| ----- | ---- | ------ | ------- |
|       |      |        |         |
|       |      |        |         |
|       |      |        |         |

##
