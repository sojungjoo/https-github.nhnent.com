---
description: 입찰 요청에 대한 응답을 처리하는 방법에 대해 설명하고 있습니다.
---

# Bid Response

## Response **Top-Level Object**

| Field   | Type         | Status   | Comment                                                                                                                                                                            |
| ------- | ------------ | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id      | string       | required | BidRequest 의 ID                                                                                                                                                                    |
| seatbid | object Array | required | 'seatbid' Object                                                                                                                                                                   |
| bidid   | string       | required | 트래킹을 위해 입찰자가 생성한 Response ID                                                                                                                                                       |
| cur     | string       | optional | 입찰가의 통화 (ISO-4217 참조)                                                                                                                                                              |
| nbr     | Integer      | optional | 응찰포기 시 사유 ([IAB OpenRTB 2.5표5.24 No-Bid Reason Codes](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=57\&zoom=100,92,450) 참조) |

### SeatBid Object

| Field | Type                   | Status   | Comment      |
| ----- | ---------------------- | -------- | ------------ |
| bid   | <p>object<br>array</p> | required | 'Bid' Object |
| seat  | string                 | optional | 입찰자의 Seat ID |

### Bid Object&#x20;

| Field   | Type         | Status   | Comment                                                                                                                                                                                                                         |
| ------- | ------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id      | string       | required | 트래킹을 위해 입찰자가 생성하는 Bid ID                                                                                                                                                                                                        |
| impid   | string       | required | BidRequest 의 'Imp' Object의 ID                                                                                                                                                                                                   |
| price   | float        | required | 입찰가 (CPM)                                                                                                                                                                                                                       |
| adid    | string       | optional | 광고의 ID                                                                                                                                                                                                                          |
| nurl    | string       | optional | AX가 낙찰된 경우 매체가 통보해 줄 AX의 Win Notice URL. nurl 호출 시 매크로 치환 필요 ([Macro](notifications.md#macro) 참고)                                                                                                                               |
| lurl    | string       | optional | AX가 입찰에 실패했을 경우 매체가 통보해 줄 AX의 Loss Notice URL                                                                                                                                                                                   |
| adm     | string       | required | <p>AX가 낙찰된 경우 매체가 통보해 줄 AX의 Win Notice URL.</p><p>nurl 호출 시 매크로 치환 필요(<a href="notifications.md#macro">Macro</a> 참고) </p>                                                                                                       |
| adomain | string array | optional | <p>광고주 도메인 리스트 </p><p>(e.g. "google.com","apple.com")</p>                                                                                                                                                                       |
| bundle  | string       | optional | <p>광고주 앱의 번들 또는 패키지 이름</p><p>(e.g. "com.nhnent.friendspop")</p>                                                                                                                                                                 |
| iurl    | string       | optional | 이미지 URL                                                                                                                                                                                                                         |
| cid     | string       | optional | 각 캠페인에 대한 유니크한 ID                                                                                                                                                                                                               |
| crid    | string       | optional | 각 크리테이티브에 대한 유니크한 ID                                                                                                                                                                                                            |
| cat     | string array | optional | <p>크리에이티브에 대한 IAB 컨텐츠 카테고리 리스트</p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=39&#x26;zoom=100,92,198">IAB OpenRTB 2.5표5.1 Content Categories</a> 참조) </p> |
| attr    | string array | optional | <p>크리에이티브 타입 리스트 </p><p>(<a href="https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf#page=50&#x26;zoom=100,92,322">IAB OpenRTB 2.5 표5.3 Creative Attributes</a> 참조)</p>             |
| dealid  | string       | optional | <p>특정 Deal에 대한 입찰일 경우 참여하는 Deal의 ID</p><p>(BidRequest.Deal.id와 동일한 값) </p>                                                                                                                                                      |
| w       | integer      | optional | 크리에이티브의 넓이 (픽셀)                                                                                                                                                                                                                 |
| h       | integer      | optional | 크리에이티브의 높이 (픽셀)                                                                                                                                                                                                                 |
| ext     | object       | optional | [Bid Object – Extension](./#bid-object-extension) 참조                                                                                                                                                                            |

### Bid Object - Extension

| Field   | Type   | Status   | Comment |
| ------- | ------ | -------- | ------- |
| bgcolor | string | optional | 배경색     |
