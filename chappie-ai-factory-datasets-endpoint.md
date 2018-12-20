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

limit: <article|video>

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
 
