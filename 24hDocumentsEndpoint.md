# 24h Documents Endpoint

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Upload Documents

API: `documents/upload`

Raw-data:

```json
  [
    {
      "id": "123",
      "type": "add|delete",
      "fields": {
        "url": "...",
        "title": "...",
        "image": "image url (Max: 250x250)",
        "description": "...",
        "source": "24h|eva",
        "published_date": "...",
        "modified_date": "...",
        "html": "article html content",
        "text": "article text content",
      }
    },
    ...
  ]
```

Return:
 `{'status': 'success'}`
  

  

  
