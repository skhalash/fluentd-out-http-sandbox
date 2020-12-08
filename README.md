# fluentd-out-http-sandbox
Playing around with fluent-plugin-out-http

## How to test?

```
docker build -t custom-fluentd:latest ./
docker network create logging
docker run -it --rm --name mock --network logging --mount type=bind,source="$(pwd)",target="/config" -p 8081:1080  mockserver/mockserver -serverPort 8081
docker run -it --rm --name custom-docker-fluent-logger --network logging custom-fluentd:latest
```
