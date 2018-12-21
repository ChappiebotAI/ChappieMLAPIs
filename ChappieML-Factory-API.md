## ChappieML AI Factory API

API endpoint: https://aa1fvz2tf6.execute-api.us-east-1.amazonaws.com/create_training_job

Method: POST

Headers: x-api-key: ***

Body form-data

Request payload as json format:
```
   {  
      "callback_url":{  
         "url":"https://api.chappie.app/v1/ml/train/callback",
         "headers":{  
            "x-api-key":"***"
         }
      },
      "dataset_endpoint":{  
         "type":"fetch",
         "url":"https://api.chappie.app/v1/ml/datasets/fetch",
         "headers":{  
            "x-api-key":"***"
         },
         "pagination":{  
            "begin_offset":0,
            "page_size":100,
            "max_pages":0
         }
      },
      "training_model":{  
         "image":"***.dkr.ecr.us-east-1.amazonaws.com/chappieai-sagemaker:slot_tagger",
         "hyperparameters":{  
            "process.train.using_gpu":"True",
            "process.train.initLearningRate":"0.2",
            "process.train.decayLearningSteps":"500",
            "process.train.decayRate":"0.95",
            "process.train.saveCheckpointSteps":"200",
            "process.train.keepCheckpointMax":"3",
            "process.train.momentum":"0.9",
            "process.train.steps":"400",
            "process.train.batchsize":"128",
            "process.eval.using_gpu":"True",
            "process.eval.steps":"100",
            "process.eval.batchsize":"15",
            "model.numClasses":"-1",
            "model.vocabSize":"-1",
            "model.embeddingSize":"50",
            "model.nHiddenGate":"50",
            "model.nHiddenTag":"50",
            "model.dropoutRate":"0.2",
            "model.add_start_end_words":"True"
         },
         "resource":{  
            "InstanceType":"ml.m4.4xlarge",
            "InstanceCount":1,
            "VolumeSizeInGB":5
         }
      },
      "task_def":"ml_tagger",
      "creator":"thaiph"
   }
```

### Example response

```
{
    "status": "success",
    "job_name": "sage-maker-train-20181221-030500"
}
```
        
 ### Request to callback_url
 
 Endpoint: callback_url
 
 Method: POST
 
 Body form-data
 
 Request payload as json format:
 
       {
        "status": "Completed",
        "TrainingEndTime": "2018-12-20 05:06:11", 
        "CreationTime": "2018-12-20 04:57:30", 
        "job_name": "lambda-tagger-job-15",
        "model": "model_download_url",
        "task_def": <ml_tagger|ml_topic>,
        "creator": <user_id|user_name>,
        "log": {
            "avg":{
               "recall":"0.57",
               "f1-score":"0.55",
               "support":"5183",
               "precision":"0.54"
            },
            "details":[
               {
                  "recall":"0.79",
                  "f1-score":"0.73",
                  "support":"3189",
                  "precision":"0.67",
                  "no":"0"
               },
               {
                  "recall":"0.28",
                  "f1-score":"0.34",
                  "support":"1287",
                  "precision":"0.41",
                  "no":"1"
               },
               {
                  "recall":"0.00",
                  "f1-score":"0.00",
                  "support":"16",
                  "precision":"0.00",
                  "no":"2"
               },
               {
                  "recall":"0.13",
                  "f1-score":"0.18",
                  "support":"260",
                  "precision":"0.30",
                  "no":"3"
               },
               {
                  "recall":"0.13",
                  "f1-score":"0.04",
                  "support":"69",
                  "precision":"0.03",
                  "no":"4"
               },
               {
                  "recall":"0.13",
                  "f1-score":"0.09",
                  "support":"46",
                  "precision":"0.06",
                  "no":"5"
               },
               {
                  "recall":"0.00",
                  "f1-score":"0.00",
                  "support":"15",
                  "precision":"0.00",
                  "no":"6"
               },
               {
                  "recall":"0.29",
                  "f1-score":"0.42",
                  "support":"62",
                  "precision":"0.75",
                  "no":"7"
               },
               {
                  "recall":"0.00",
                  "f1-score":"0.00",
                  "support":"43",
                  "precision":"0.00",
                  "no":"8"
               },
               {
                  "recall":"0.00",
                  "f1-score":"0.00",
                  "support":"14",
                  "precision":"0.00",
                  "no":"9"
               },
               {
                  "recall":"0.00",
                  "f1-score":"0.00",
                  "support":"182",
                  "precision":"0.00",
                  "no":"10"
               }
            ]
         }
       }


## API to get list training job

Endpoint: https://aa1fvz2tf6.execute-api.us-east-1.amazonaws.com/check_trained_job

Method: POST

Headers: x-api-key: ***

### Example response
```
[
    {
        "TrainingJobStatus": "InProgress",
        "TrainingJobName": "sage-maker-train-20181220-162120",
        "CreationTime": "2018-12-20 16:21:37"
    },
    {
        "TrainingJobStatus": "Completed",
        "TrainingJobName": "sage-maker-train-20181220-155655",
        "CreationTime": "2018-12-20 15:57:12",
        "TrainingEndTime": "2018-12-20 16:05:59"
    }
    ...
]

```

## API to stop training job

Endpoint: https://aa1fvz2tf6.execute-api.us-east-1.amazonaws.com/stop_training_job

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
    "status": "error",
    "message": "An error occurred (ValidationException) when calling the StopTrainingJob operation: The request was rejected because the training job is in status Completed."
}

```


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
