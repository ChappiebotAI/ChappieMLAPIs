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
        "description": "...",
        "source": "24h|eva",
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

  
