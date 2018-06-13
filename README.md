# ChappieMLAPIs
Chappie Machine Learning APIs

# Name Entity Recognition

API endpoint: https://f130s6e04g.execute-api.us-east-1.amazonaws.com/prod/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Tagging

API: `ml/tagging`

Form-data:
  `sent`: string
  `request_id`: string (optional)

Return:
 `[(token/tag), (token/tag), (token/tag), ...]`
  
CURL example:

```bash
curl 
  -d "sent=bán xe cũ Mazda 3 đời 2017 chính chủ&request_id=12345" 
  -H "x-api-key: ***" 
  -X POST https://f130s6e04g.execute-api.us-east-1.amazonaws.com/prod/v1/ml/tagging
```
  
## Classify

API: `ml/classify`

Form-data:
  `sent`: string
  `request_id`: string (optional)
  
Return:
 `[(topic/score), (topic/score), (topic/score), ...]`
  
CURL example:

```bash
curl 
  -d "sent=bán xe cũ Mazda 3 đời 2017 chính chủ&request_id=12345" 
  -H "x-api-key: ***" 
  -X POST https://f130s6e04g.execute-api.us-east-1.amazonaws.com/prod/v1/ml/classify
```
  
