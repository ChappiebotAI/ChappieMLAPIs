# ChappieMLAPIs
Chappie Machine Learning APIs

API endpoint: https://api.chappie.app/v1/


# Name Entity Recognition

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Tagging

API: `ml/tagging`

Form-data:
  `sent`: string
  `readability`: 1
  `request_id`: string (optional)

Return:
 `[(token/tag), (token/tag), (token/tag), ...]`
  
CURL example:

```bash
curl 
  -d "sent=bán xe cũ Mazda 3 đời 2017 chính chủ&readability=1&request_id=12345" 
  -H "x-api-key: ***" 
  -X POST https://api.chappie.app/v1/ml/tagging
```
  
## Classify

API: `ml/classify`

Form-data:
  `sent`: string
  `readability`: 1
  `request_id`: string (optional)
  
Return:
 `[(topic/score), (topic/score), (topic/score), ...]`
  
CURL example:

```bash
curl 
  -d "sent=bán xe cũ Mazda 3 đời 2017 chính chủ&readability=1&request_id=12345" 
  -H "x-api-key: ***" 
  -X POST https://api.chappie.app/v1/ml/classify
```
  
