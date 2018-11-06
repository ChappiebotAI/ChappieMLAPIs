# 24h Recommendation APIs

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Related

API: `related`

Getrecommended items.

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
  'url' => 'https://www.24h.com.vn/bong-da/ronaldinho-co-nguy-co-bi-truy-na-tai-khoan-chi-co-160000-dong-c48a1002950.html'
), NULL);

$request->setRequestUrl('https://api.chappie.app/v1/related');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'cache-control' => 'no-cache',
  'x-api-key' => '***'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```
  
