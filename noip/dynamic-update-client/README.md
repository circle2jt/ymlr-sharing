# noip dynamic-update-client
Update client ip to no-ip ( DUC )

## Run via CLI
```sh
  npx ymlr 
    -e USERNAME=${USERNAME} \
    -e PASSWORD=${PASSWORD} \
    -e IP=${IP} \
    -e HOSTNAME=${HOSTNAME} \
    -e INTERVALTIME=${INTERVALTIME}
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/github/npm-up-version/index.yaml
```
Example: 
```sh
  npx ymlr \
    -e USERNAME=test \
    -e PASSWORD=testpassword \
    -e IP=123.23.23.23 \
    -e HOSTNAME=test.ddns.net \
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/noip/dynamic-update-client/index.yaml
```

## Run in a docker
```sh
  docker run --rm -it --name auto-update-noip-client \
    -e USERNAME=${USERNAME} \
    -e PASSWORD=${PASSWORD} \
    -e IP=${IP} \
    -e HOSTNAME=${HOSTNAME} \
    -e INTERVALTIME=${INTERVALTIME}
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/noip/dynamic-update-client/index.yaml
```
- `USERNAME`:         Username login noip
- `PASSWORD`:         Password login noip
- `IP`:               IP client which is mapped to hostname
- `HOSTNAME`:         Hostname which is need to update a new ip
- `INTERVALTIME`:     Loop to re-update if ip is changed. 60s, 1m, 1h ... Default is no loop. [Unit time](https://github.com/circle2jt/ymlr?tab=readme-ov-file#sleep)