

# EFK Stack

## Deploy

```shell
docker compose up -d
```

## Sample log matching elasticsearch
```shell
echo '{"spanId":"172170139140","traceId":"3123213123","name":"Foo"}'|fluent-cat elasticsearch.test
```

## cURL to fluentd http port
```shell
curl -X POST -H "Content-Type: application/json" -d '{"message": "Hello World!"}' http://localhost:9880 
```

## Bibliography 

- [Deploying an EFK Stack with Docker](https://adamtheautomator.com/efk-stack/)
- [Forwarding logs to elasticsearch using fluentd](https://gist.github.com/skhatri/48a6119f0ef20e5e042dc97d1011f37a)