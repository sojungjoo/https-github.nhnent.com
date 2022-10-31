# Bid Response sample

## Banner 광고 응답 예시&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
{
    "id": "1234567890",
    "bidid": "abc1123",
    "cur": "USD",
    "seatbid": [
        {
            "seat": "512",
            "bid": [
                {
                    "id": "1", 
                    "impid": "102", 
                    "price": 9.43,
                    "nurl": " https://adx-exchange.toast.com/nurl?impid=102&wc=${AUCTION_PRICE}",
                    "lurl": " https://adx-exchange.toast.com/lurl?impid=102&lossreason=${AUCTION_LOSS}",
                    "adm": "<!DOCTYPE html><html>....$(TTX_CLICK_URL)....</html>",
                    "iurl": " https://adx-exchange.toast.com/pathtosampleimage",
                    "adomain": [ "advertiserdomain.com" ],
                    "bundle": [ "com.advertiserdomain.app" ],
                    "cid": "campaign111",
                    "crid": "creative112",
                    "attr": [ 1, 2, 3, 4, 5, 6, 7, 12 ],
                    "dealid": "abcd123",
"cat": [ "IAB7-4" ],
                    "w": 300,
                    "h": 250,
                    "ext": {
                              "bgcolor": "#FFFFFF"
}
                }
            ]
        }
    ]
}

```
{% endcode %}

## Native 광고 응답 예시&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
{
    "id": "1234567890",
    "bidid": "abc1123",
    "cur": "USD",
    "seatbid": [
        {
            "seat": "512",
            "bid": [
                {
                    "id": "1", 
                    "impid": "102", 
                    "price": 9.43,
                    "nurl": "https://adx-exchange.toast.com/nurl?impid=102&wc=${AUCTION_PRICE}",
                    "lurl": "https://adx-exchange.toast.com/lurl?impid=102&lossreason=${AUCTION_LOSS}",
                    "adm": "{\"native\":{\"ver\":\"1.2\",\"link\":{ ... },\" assets\":[ ... ]}}",
                    "iurl": " https://adx-exchange.toast.com/pathtosampleimage",
                    "adomain": [ "advertiserdomain.com" ],
                    "bundle": [ "com.advertiserdomain.app" ],
                    "cid": "campaign111",
                    "crid": "creative112",
                    "attr": [ 1, 2, 3, 4, 5, 6, 7, 12 ],
                    "dealid": "abcd123",
"cat": [ "IAB7-4" ],
                    "w": 300,
                    "h": 250,
                    "ext": {
                              "bgcolor": "#FFFFFF"
}
                }
            ]
        }
    ]
}

```
{% endcode %}
