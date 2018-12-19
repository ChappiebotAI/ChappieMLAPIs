## ChappieML AI Factory API

API endpoint: https://aa1fvz2tf6.execute-api.us-east-1.amazonaws.com/prod

Method: POST

Headers: x-api-key: ***

Body form-data

Request payload as json format:

        {
          "job_name": "lambda-tagger-job-12",
          "callback_url": "https://api.chappie.app/v1/callback_status",
          "training_image": "065056466896.dkr.ecr.us-east-1.amazonaws.com/chappieai-sagemaker:slot_tagger"
        }
        
### Example response

        {
            "Status": "Success! Training in process"
        }
        
 ### Response to callback_url
       {
          'model_path':'url_to_download_model'
       }
