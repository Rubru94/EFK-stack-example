

# EFK Stack

## Deploy

```shell
docker compose up -d
```
## cURL to consume API rest

```
http://localhost:9200/span-*/_search?filter_path=hits.total.value,hits.hits.fields
```

## fluentd logs

  - ## Sample log
    ```shell
    echo '{"spanId":"172170139140","traceId":"3123213123"}'|fluent-cat span-2023.03.31
    ```
    

  - ## cURL to fluentd http port
    ```shell
    curl -X POST -H "Content-Type: application/json" -d '{"spanId":  "000000", "traceId":"111111", "foo":{"a": "a", "b": "b"}, "array"[{"a":"a"}, {"b": "b"}]}' http://localhost:9880/span-2023.03.31
    ```

  - ## RabbitMQ

    - **Queue message**:
  
      - *Headers*: 
          ```
          Content-Type: application/json
          ```
      
      - *Payload*: 
          ```
          {"spanId": "000000", "traceId":"111111", "foo":{"a":"a", "b":"b"}, "array": [{"a":"1"}, {"b": "2"}]}
          ```

## fluent.conf

    - index_name --> Fixed index name
    - logstash_prefix --> Change the index prefix

## Index Template
    - index.lifecycle.name --> specifies the name of the lifecycle policy to apply to new indices that match the index pattern.
    - index.lifecycle.rollover_alias --> specifies the index alias to be rolled over when the rollover action is triggered for an index.



## Bibliography 

- [Deploying an EFK Stack with Docker](https://adamtheautomator.com/efk-stack/)
- [Forwarding logs to elasticsearch using fluentd](https://gist.github.com/skhatri/48a6119f0ef20e5e042dc97d1011f37a)