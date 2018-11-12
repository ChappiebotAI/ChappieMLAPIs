# 24h Recommendation APIs

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Related

API: `related`

Get recommended items.

Params:

```
client_id: <number> application id have provided by Chappiebot. 

content_type: <article|video>

limit: maximum returning related's items (1 to 30)

user_id: issued by application (facebook messenger, web...)

document_id: (optional) hash string of url

url: (24h or eva website url)

utm_campaign: string append to delevery url

ref: reference param append to delevery url
```

Response:
 ```
 {
    "items": [ // list of related documents with current document
     {
      "document_id": "<unique id with 11 chars>",
      "title": "<document title>",
      "description": "<document description>",      
      "url": "<delivered url>",      
      "origin_url": "<origin url>",      
      "media": "...",
      "source: "...",
      "score": <float number: 0 to 1>,
      "published_date": <date in ios format>,
      "images": [<list of images url>],
      "image": "cover image"      
     },
     ...
    ],
    "document": { // current document by url
      "document_id": "<unique id with 11 chars>",
      "title": "<document title>",
      "description": "<document description>",      
      "url": "<web url>",      
      "media": "...",
      "source: "...",
      "published_date": <date in ios format>,
      "image": "cover image"      
    },
    "entities": [ // list of entity extracted from document html
      [
        "entity title", 
        "entity key"
       ]
    ]
 }
 ```
 
**Example response**

```json
{
    "items": [
        {
            "description": "Romelu Lukaku bị HLV Jose Mourinho đày ải trên băng ghế dự bị ở trận thắng Everton mới đây. Và một lần nữa “Voi rừng đệ nhị” lại bị các CĐV MU chỉ trích thậm tệ.",
            "title": "Lukaku 9 trận \"tịt ngòi\": Sút 4 vào 1 còn chê, lỗi tại MU & Mourinho?",
            "url": "https://a.24h.com.vn/click?r=https%3A%2F%2Fwww.24h.com.vn%2Fbong-da%2Flukaku-9-tran-tit-ngoi-sut-4-vao-1-con-che-loi-tai-mu-mourinho-c48a1002202.html%3Futm_source%3Dchappie-messenger%26utm_medium%3Drecommend%26utm_campaign%3Drelated&t=Tm9uZSxvN3ZuemxncWs5aiwwLjU2OTM2OTQxMDA3OTQ1NixjbGlja19yZWxhdGVkLDE1NDE1NTc5NzUuMSw2LDAsNGU2N2QxOWVlZTMzMTFhYzFlMzViMmI0YWZmZmRhODMsNjhiMGE1NDdkZTIyMTliY2RjMzE3OWQxOTEwNGM3Y2JmNDEyOTlhZTQ2OTIzMWJmN2JjMTU4MDg3MWY0NDYzNg%3D%3D",
            "media": null,
            "image": "https://image.24h.com.vn/upload/4-2018/images/2018-11-03/640480-1541200200-659-width640height480.jpg",
            "source": "https://www.24h.com.vn/upload/rss/bongda.rss",
            "score": 0.5692465745499361,
            "published_date": "2018-11-03T06:10:00Z",
            "images": [
                "https://image-us.24h.com.vn/upload/4-2018/images/2018-11-03/Lukaku-9-tran-tit-ngoi-Sut-4-vao-1-con-che-loi-tai-MU-c1759-1534003958-800-1541200113-16-width660height440.jpg",
                "https://image-us.24h.com.vn/upload/4-2018/images/2018-11-03/Lukaku-9-tran-tit-ngoi-Sut-4-vao-1-con-che-loi-tai-MU-ipanews_18552f1d-fea4-45d6-bb91-d284bf2f38ae_embed-1541199993-168-width660height482.jpg",
                "https://image-us.24h.com.vn/upload/4-2018/images/2018-11-03/Lukaku-9-tran-tit-ngoi-Sut-4-vao-1-con-che-loi-tai-MU-skysports-alvaro-morata-sergio-aguero-harry-kane-r-1541200135-146-width660height371.jpg"
            ],
            "document_id": "o7vnzlgqk9j"
        }      
    ],
    "document": {
        "source": "www.24h.com.vn",
        "description": "Kylian Mbappe vừa vượt qua hai siêu sao Neymar Junior và Harry Kane để trở thành cầu thủ được định giá có giá trị chuyển nhượng cao nhất thế giới bóng đá. Trong khi đó, Cristiano Ronaldo thậm chí không lọt vào top 10.",
        "title": "Vua chuyển nhượng: Mbappe phế ngôi Neymar, cho Ronaldo hít khói",
        "url": "https://www.24h.com.vn/bong-da/vua-chuyen-nhuong-mbappe-phe-ngoi-neymar-cho-ronaldo-hit-khoi-c48a1002896.html",
        "image": "https://image.24h.com.vn/upload/4-2018/images/2018-11-06/64x0480-1541461117-617-width640height480.jpg",
        "published_date": "2018-11-06T19:01:00Z",
        "document_id": "dg1wvw6r4kj"
    },
    "entities": [
        [
            "Chuyển nhượng",
            "D2-Chuyển nhượng"
        ],
        [
            "Bóng đá",
            "D1-Bóng đá"
        ],
        [
            "Neymar Junior",
            "Neymar Junior/Person"
        ],
        [
            "Harry Kane",
            "Harry Kane/Person"
        ],
        [
            "Mbappe",
            "Mbappe/Person"
        ],
        [
            "PSG",
            "PSG/Organization"
        ],
        [
            "Ronaldo",
            "Ronaldo/Person"
        ],
        [
            "CIES",
            "CIES/Organization"
        ],
        [
            "World Cup 2018",
            "World Cup 2018/Event"
        ],
        [
            "Messi",
            "Messi/Person"
        ]
    ]
}
```
 
 
## Extraction

API: `related`

Document extraction

Params:

```
client_id: <number> application id have provided by Chappiebot. 

document_id: (optional) hash string of url

url: (24h or eva website url)

```

Response:
 ```
 {
    "tokens": [ // list of tokens  
    ],
    "entities": [ // list of entities       
    ],
    "topics": [ // list of topics
    ],
    "document": { // current document by url
      "document_id": "<unique id with 11 chars>",
      "title": "<document title>",
      "description": "<document description>",      
      "url": "<web url>",      
      "media": "...",
      "source: "...",
      "published_date": <date in ios format>,
      "image": "cover image"      
    },
    "best_entity": [
        "Neymar Junior",
        "Person"
    ]
}
 ``` 
  

## Code Examples

### PHP

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->addForm(array(
  'client_id' => '6',
  'url' => 'https://www.24h.com.vn/bong-da/vua-chuyen-nhuong-mbappe-phe-ngoi-neymar-cho-ronaldo-hit-khoi-c48a1002896.html'
), NULL);

$request->setRequestUrl('https://api.chappie.app/v1/extraction');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'x-api-key' => '***'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```
  
  
### Python
```python
import requests

url = "https://api.chappie.app/v1/extraction"

headers = {
    'x-api-key': "***",
    }
    
payload = {
  'client_id': 6,
  'url': 'https://www.24h.com.vn/bong-da/vua-chuyen-nhuong-mbappe-phe-ngoi-neymar-cho-ronaldo-hit-khoi-c48a1002896.html'
}

response = requests.request("POST", url, json=payload, headers=headers)

print(response.json)
```

**Example response**

```json
{
    "tokens": [
        "cầu thủ",
        "thẩm định",
        "siêu sao người",
        "giải đấu",
        "tiền đạo",
        "màn trình diễn đỉnh cao",
        "giá trị cao nhất thế giới bóng đá",
        "giá trị cao nhất thế giới",
        "bứt tốc",
        "thi đấu chói sáng"
    ],
    "entities": [
        [
            "Neymar Junior",
            "Neymar Junior/Person"
        ],
        [
            "Harry Kane",
            "Harry Kane/Person"
        ],
        [
            "Mbappe",
            "Mbappe/Person"
        ],
        [
            "PSG",
            "PSG/Organization"
        ],
        [
            "Ronaldo",
            "Ronaldo/Person"
        ],
        [
            "CIES",
            "CIES/Organization"
        ],
        [
            "World Cup 2018",
            "World Cup 2018/Event"
        ],
        [
            "Messi",
            "Messi/Person"
        ]
    ],
    "topics": [
        [
            "Chuyển nhượng",
            "D2-Chuyển nhượng"
        ],
        [
            "Bóng đá",
            "D1-Bóng đá"
        ]
    ],
    "document": {
        "description": "Kylian Mbappe vừa vượt qua hai siêu sao Neymar Junior và Harry Kane để trở thành cầu thủ được định giá có giá trị chuyển nhượng cao nhất thế giới bóng đá. Trong khi đó, Cristiano Ronaldo thậm chí không lọt vào top 10.",
        "title": "Vua chuyển nhượng: Mbappe phế ngôi Neymar, cho Ronaldo hít khói",
        "url": "https://www.24h.com.vn/bong-da/vua-chuyen-nhuong-mbappe-phe-ngoi-neymar-cho-ronaldo-hit-khoi-c48a1002896.html",
        "image": "https://image.24h.com.vn/upload/4-2018/images/2018-11-06/64x0480-1541461117-617-width640height480.jpg",
        "source": "www.24h.com.vn",
        "published_date": "2018-11-06T19:01:00Z",
        "document_id": "dg1wvw6r4kj"
    },
    "best_entity": [
        "Neymar Junior",
        "Person"
    ]
}
```

# 24h Documents Endpoint

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Upload Documents

API: `documents/upload`

Upload multi documents at time.

Request payload as json format:

```json
  [
    {
      "id": "123", (optional)
      "type": "add|delete",
      "fields": {
        "url": "...",
        "title": "...",
        "image": "article's avatar image url",
        "content_type": "article|video|ad",
        "media": "video url (optional)",
        "description": "...",
        "source": "www.24h.com.vn|eva.vn",
        "published_date": "...",
        "modified_date": "... (optional)",
        "html": "article html content",
        "text": "article text content (optional)",
      }
    },
    ...
  ]
```

Response:
 `{'status': 'success'}`
  
If `type` == `delete`, you set attribute `fields={}`.

## Delete document with url

```json
  [
    {
      "type": "delete",
      "fields": {
        "url": "...",
      }
    },
    ...
  ]
```

  

