## ChappieML AI Factory API

API endpoint: https://aa1fvz2tf6.execute-api.us-east-1.amazonaws.com/prod

Method: POST

Headers: x-api-key: ***

Body form-data

Request payload as json format:

        {
          "job_name": "lambda-tagger-job-12",
          "callback_url": "https://api.chappie.app/v1/callback_status",
          "dataset_endpoint": "https://api.chappie.app/v1/ml/datasets/fetch",
          "training_image": "065056466896.dkr.ecr.us-east-1.amazonaws.com/chappieai-sagemaker:slot_tagger"
        }
        
### Example response

        {
            "Status": "Success! Training in process"
        }
        
 ### Request to callback_url
 
 Endpoint: callback_url
 
 Method: POST
 
 Body form-data
 
 Request payload as json format:
 
       {
          'model_path':'url_to_download_model'
       }


## API to check training status

Endpoint: https://d5r1if03rg.execute-api.us-east-1.amazonaws.com/prod

Method: POST

Headers: x-api-key: ***

Body form-data

Request payload as json format:
```
{
  "job_name": "tagger-train-model-08"
}
```

### Example response
```
{
    "status": "InProgress"
}
```
