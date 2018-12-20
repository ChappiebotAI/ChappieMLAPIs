# Chappie AI Factory Datasets Endpoint

API endpoint: https://api.chappie.app/v1/

Method: POST

Headers: 
  `x-api-key: ***`

Body form-data

## Fetch train samples

API: `ml/datasets/fetch`

Fetch train samples.

Params:

```
offset: <number> 

page_size: maximum returning related's items (1 to 500)

```

Response:
 ```
{
  'datasets': datasets,
  'type': type, 
  'offset': offset, 
  'page_size': page_size    
}
 ```
 

## Fetch train labels

API: `ml/labels/fetch`

Fetch train samples.

Params:

```
type: <tagger|topic> 

fields: id, title (optional)

```

Response:
 ```
{
  'datasets': datasets,
  'type': type, 
  'offset': offset, 
  'page_size': page_size    
}
 ```
 
 
## Callback to AI Factory

API: `ml/train/callback`

Post training job payloads to AI Factory.

Params:

```
{
  'status': <succeeded|failed|deleted|pending>,
  'task_id': <string>,
  'task_def': <ml_tagger|ml_topic>,
  'creator': <user_id>
  
}

```

Response:
 ```
{
  'status': <string>,
}
 ```
 
 
