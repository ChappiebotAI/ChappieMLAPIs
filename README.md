# ChappieMLAPIs
Chappie Machine Learning APIs

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Tagging (Name Entity Recognition)

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
  
## API Pipelines
You can invoke multiple api at the same time with only one calling.

API: `v1/pipelines`

Example: 

```json
[
  ["ml/push", "Xe Cũ Land Rover Range Rover Autobiography LWB 2014", {"exclude": 1}],
  ["ml/tagging", {"sent": ":0", "readability": 1}],
  ["ml/tagging/entity", {"tagging": ":1", "readability": 1}],
  ["ml/tagging/value", {"tagging": ":1", "readability": 1}]	
]
```


```json
[
  ["ml/push", "Xe Cũ Land Rover Range Rover Autobiography LWB 2014", {"exclude": 1}],
  ["ml/classify", {"sent": ":0", "readability": 1}],
  ["ml/tagging", {"sent": ":0", "readability": 1}],
  ["ml/tagging/entity", {"tagging": ":2", "readability": 1}],
  ["ml/tagging/value", {"tagging": ":2", "readability": 1}]	
]
```

  
