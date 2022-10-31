# Bid Request Sample

## Web 광고 요청 예시&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
{
    "id": "80ce30c53c16e6ede735f123ef6e32361bfc7b22",
    "at": 1,
    "cur": [ "USD","KRW" ],
    "imp": [
        {
            "id": "1",
            "tagid": "0Qv35",
            "bidfloor": 0.03,
            "bidfloorcur": "USD",
            "secure": 1,
            "banner": {
                "h": 250,
                "w": 300,            },
               "pmp": {
                 "private_auction": 0,
                 "deals": [
                   {
                       "id":"abcd123",
                       "at": 3, 
                       "bidfloor": 1.25,
                       "bidfloorcur": "USD"
                 } ]
               }
        }
    ],
    "site": {
       "id": "102855",
       "cat": [ "IAB3-1" ],
       "domain": "nhnace.com",
       "page": "https://www.nhnace.com/1234.html ",
         "mobile": 0
    },
    "device": {
        "ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_6_8) AppleWebKit/537.13 (KHTML, like Gecko) Version/5.1.7 Safari/534.57.2",
        "ip": "123.145.167.10"
    },
    "user": {
       "id": "55816b39711f9b5acf3b90e313ed29e51665623f"
    },
    "source": {
       "tid": "55816b39711f9b5acf3b90e313ed29e51665623f"
    }
}

```
{% endcode %}

## App 광고 요청 예시&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
{
    "id": "IxexyLDIIk",
    "at": 2,
    "bcat": [ "IAB25", "IAB7-39", "IAB8-18", "IAB8-5", "IAB9-9" ],
    "badv": [ "apple.com", "go-text.me", "heywire.com" ],
    "imp": [
        {
            "id": "1",
            "tagid": "0Qv35",
            "bidfloor": 0.5,
            "bidfloorcur": "USD",
            "banner": {
                "w": 728,
                "h": 90,
                "pos": 1,
                "btype": [ 4 ],
                "battr": [ 14 ]
            },
               "pmp": {
                 "private_auction": 0,
                 "deals": [
                   {
                       "id":"abcd123",
                       "at": 3, 
                       "bidfloor": 1.25,
                       "bidfloorcur": "USD"
                 } ]
               }
        }
    ],
    "app": {
        "id": "agltb3B1Yi1pbmNyDAsSA0FwcBiJkfIUDA",
        "name": "adlib project",
        "cat": [ "IAB15", "IAB15-10" ],
        "bundle": "test.adlib.project"
        },
    "device": {
        "ua": "Mozilla/5.0 (iPhone; CPU iPhone OS 6_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9A334 Safari/7534.48.3",
        "ip": "123.145.167.189",
        "make": "Apple",
        "model": "iPhone",
        "os": "iOS",
        "osv": "6.1",
        "devicetype": 1,
        "geo": {
            "lat": 35.012345,
            "lon": -115.12345,
            "type": 1,
"country": "KOR"
        },
        "ifa": "TEST-TEST-TEST-TESTPAGE",
    },
    "user": {
        "id": "ffffffd5135596709273b3a1a07e466ea2bf4fff"
    },
    "source": {
       "tid": "55816b39711f9b5acf3b90e313ed29e51665623f"
    }
}

```
{% endcode %}

## Native 광고 요청 예시&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
{
    "id": "80ce30c53c16e6ede735f123ef6e32361bfc7b22",
    "at": 1,
    "cur": [ "USD","KRW" ],
    "imp": [
        {
            "id": "1",
            "tagid": "0Qv35",
            "bidfloor": 0.03,
            "bidfloorcur": "USD",
            "secure": 1,
            "native": {
                  "request": "{\"native\":{\"ver\":\"1.2\",\"context\":2 ....",
                  "ver": "1.2",
                  "api": [
                      3
                  ],
                  "battr": [
                    13,
                    14
                  ]
              }
        }
    ],
    "site": {
       "id": "102855",
       "cat": [ "IAB3-1" ],
       "domain": "nhnace.com",
       "page": "https://www.nhnace.com/1234.html ",
         "mobile": 0
    },
    "device": {
        "ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_6_8) AppleWebKit/537.13 (KHTML, like Gecko) Version/5.1.7 Safari/534.57.2",
        "ip": "123.145.167.10"
    },
    "user": {
       "id": "55816b39711f9b5acf3b90e313ed29e51665623f"
    },
    "source": {
       "tid": "55816b39711f9b5acf3b90e313ed29e51665623f"
    }
}

```
{% endcode %}
