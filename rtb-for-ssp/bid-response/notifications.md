# Notifications

## 응찰포기방법

AX는 응찰 포기 시 HTTP Response Status Code에 204 ("No Content")를 반환합니다.

## Macro

경매에서 낙찰된 경우, AX는 낙찰 가격을 전달받기 위해 'nurl'(Win Notice URL)과 'adm'(AdMarkup)에 ${AUCTION\_PRICE}를 추가합니다. 매체는 매크로를 치환하여 낙찰가를 전송해야 합니다.

### Macro종류

| Macro                 | Comment                                               |
| --------------------- | ----------------------------------------------------- |
| ${AUCTION\_PRICE}     | 낙찰 가격                                                 |
| ${AUCTION\_PRICE:dcp} | 암호화된 낙찰 가격 사전 협의를 통해 가격 암호화 설정을 한 경우에만 해당 매크로를 사용합니다. |

### Macro 사용예시&#x20;

{% tabs %}
{% tab title="A. Win notice URL 매크로 사용 예시" %}
{% code overflow="wrap" lineNumbers="true" %}
```
"bid": [
    {
        "id": "1",
        "nurl":"https://adx-exchange.toast.com/a_win?pub_code=12341234&area_code=43214321&wc=${AUCTION_PRICE}",
        ....
    }
]

```
{% endcode %}
{% endtab %}

{% tab title="B. Adm 매크로 사용 예시 (Banner)" %}
{% code lineNumbers="true" %}
```
"bid": [
    {
        "id": "1",
        "adm": "<!DOCTYPE html><html>)....${AUCTION_PRICE}....</html>",
        ....
    }
]

```
{% endcode %}
{% endtab %}

{% tab title="C. Adm 매크로 사용 예시 (Native)" %}
{% code overflow="wrap" lineNumbers="true" %}
```
"bid": [
    {
        "id": "1",
        "adm":"{\"native\":{\"ver\":\"1.2\",\"link\":{...},\"imptrackers\":[...https://alpha-adserver.toast.com/a_imp?wc=${AUCTION_PRICE}...,\"assets\":[ ... ]}}",
        ....
    }
]

```
{% endcode %}
{% endtab %}
{% endtabs %}
