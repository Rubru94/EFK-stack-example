

# EFK Stack

## Deploy

```shell
docker compose up -d
```

## Sample log matching elasticsearch
```shell
echo '{"spanId":"172170139140","traceId":"3123213123"}'|fluent-cat span-2023.03.30
```

## cURL to fluentd http port
```shell
curl -X POST -H "Content-Type: application/json" -d '{"spanId": "000000", "traceId":"111111", "foo":{"a": "a", "b": "b"}, "array": [{"a":"a"}, {"b": "b"}]}' http://localhost:9880/span-2023.03.30 
```

## fluent.conf

    index_name --> Fixed index name
    logstash_prefix --> Change the index prefix

## Bibliography 

- [Deploying an EFK Stack with Docker](https://adamtheautomator.com/efk-stack/)
- [Forwarding logs to elasticsearch using fluentd](https://gist.github.com/skhatri/48a6119f0ef20e5e042dc97d1011f37a)