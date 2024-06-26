# portainer-to-gatus-config
Auto generate to gatus config from stacks in the portainer

## 1. Config in gatus to support load multiple configuration files
Add `GATUS_CONFIG_PATH` env to path of gatus config directory.

## 2. Config in a stack in a portainer
- Add `gatus` labels in a stack configuration in a portainer

> Example:
```yaml
services:
  redis:
    image: redis:alpine
    container_name: redis
    restart: always
    ports:
      - 6379:6379/tcp
    labels:
      gatus: |
        url: "tcp://redis:6379"
        interval: 30s
        conditions:
          - "[CONNECTED] == true"
        alerts:
          - type: telegram
            send-on-resolved: true
```

## 3. Run in a docker
#### Run with an access token
```sh
  docker run --rm -it --name gatus-portainer \
    -v /gatus/config:/gatus/config:rw,rshared \
    -e url=${PORTAINER_URL} \
    -e token=${PORTAINER_TOKEN} \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/gatus/portainer-to-gatus-config/index.yaml
```
- `PORTAINER_URL`:      portainer url
- `PORTAINER_TOKEN`:    user access token in portainer

#### Run with username/password
```sh
  docker run --rm -it --name gatus-portainer \
    -v /gatus/config:/gatus/config:rw,rshared \
    -e url=${PORTAINER_URL} \
    -e username=${PORTAINER_USER} \
    -e password=${PORTAINER_PASS} \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/gatus/portainer-to-gatus-config/index.yaml

```
- `PORTAINER_URL`:      portainer url
- `PORTAINER_USER`:     username in portainer
- `PORTAINER_PASS`:     password in portainer

# Addition
Allow add multiple gatus config in a service in stacks
```yaml
# stack name in portainer is `infra`
services:
  redis:
    image: redis:alpine
    container_name: redis_container_name
    restart: always
    ports:
      - 6379:6379/tcp
    labels:
      gatus: |
        - url: "tcp://redis:6379"       # name => "infra/redis/redis_container_name"
          interval: 30s
          conditions:
            - "[CONNECTED] == true"
          alerts:
            - type: telegram
              description: Redis in my_server is down
              send-on-resolved: true
        - name: $name-ping              # name => "infra/redis/redis_container_name-ping"
          url: "icmp://my_server"
          conditions:
            - "[CONNECTED] == true"
          alerts:
            - type: telegram
              description: my_server is down
              send-on-resolved: true
```
