# ChappieAPIsFramework

A light-weight http server apis to deploy machine learning pipelines.


## Concepts

How `pipeline` works

```python
    class A(BasePipe):
        def fit(self, x):
            return x + 1


    class B(BasePipe):
        def __init__(self, x):
            super(B, self).__init__()
            self.x = x

        def fit(self, x):
            return x * self.x


    class C(BasePipe):
        def predict(self, x):
            return x * x

    f = Pipeline((
        A(),
        B(2),
        C()))
    x = 3
    print(f.fit(x))
```

Transform a `pipeline` to an `api`.


`apis/hello.py`
```python
from pipeline import BasePipe, Pipeline
from factory import Factory


# Develop your features with pipelines

class Hello(BasePipe):

    def initialize(self):
        self.add_task(self.callback, 'hello', {'delay': 10})

    def on_begin(self):
        # handle request begins
        pass

    def on_end(self, response):
        # handle request ends
        pass

    def fit(self, message):

        # get request params
        params = self.context.params

        # add a task to quene and run in background
        # self.add_task(self.callback, message, {'delay': 5})
        # self.add_task(self.callback, message)

        return message

    def callback(self, response):
        '''
        do something here: logging, send email or push notification
        callback(response) will be add to stacks of a worker.
        Then, its will be execute by worker in a thread.
        '''
        print('callback!')



def decoder(self, message):
    return {
        'message': message
    }


# Create the factory to transforming the pipeline into api

class HelloFactory(Factory):
    '''
    API
    Headers: <self.api_key>
    x-api-key:
    '''

    def __init__(self, app):
        super(HelloFactory, self).__init__(app)

        self.api_key = app.settings.get('factory.api_key')

    # v1/hello
    def hello(self):
        return Pipeline((
            Hello(),
            decoder
        ))
```

`application.py`
```python
from factory import BaseApplication
from apis.hello import HelloFactory


class Application(BaseApplication):

    def __init__(self, app):
        super(Application, self).__init__(app)

        self.add_factory(HelloFactory)
```


## Setup your development project with ChappieAPIsFramework (chappiefw)

```bash

# Go to your project folder. Eg: `/project/myapp`
cd project/myapp

virtualenv venv
source venv/bin/activate

# install the framework
pip install dist/chappiefw-1.0.tar.gz

# start your app fist time, the apis will be serve at http://localhost:8001/v1
uwsgi --ini-paste development.ini
```

## Tests

You can uses `Postman` to test the apis

*Request:*
```
URL: http://localhost:8001/v1
Method: POST
Headers
    x-api-key: <factory.api_key in development.ini>
Body
    form-data
    Key: message
    Value: hello world
```

*Response:*
```json
{
    "message": "hello world"
}
```

Perfect! Now you can open your project's workspace and write your first code in `/apps` folder
and `application.py`


## Build and run as a Docker container

```bash
# docker container run as port 80. Your apis: http://localhost/v1/
./docker-run.sh

./docker-stop.sh
```

