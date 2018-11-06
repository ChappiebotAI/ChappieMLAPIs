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
client_id: 6

url: (24h or eva website url)
```

Response:
 ```json
 {
    "items": [
    ],
    "document": {
    },
    "entities": [
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

$request->setRequestUrl('https://api.chappie.app/v1/related');
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

url = "https://api.chappie.app/v1/related"

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
