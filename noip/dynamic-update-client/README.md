# noip dynamic-update-client
Update client ip to no-ip ( DUC )

## Run via CLI
```sh
  npx ymlr 
    -e USERNAME=${USERNAME} \
    -e PASSWORD=${PASSWORD} \
    -e HOSTNAME=${HOSTNAME} \
    -e IP=${IP} \
    -e INTERVALTIME=${INTERVALTIME}
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/github/npm-up-version/index.yaml
```
Example: 
```sh
  npx ymlr \
    -e USERNAME=test \
    -e PASSWORD=testpassword \
    -e HOSTNAME=test.ddns.net \
    -e IP=123.23.23.23 \
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/noip/dynamic-update-client/index.yaml
```

## Run in a docker
```sh
  docker run --rm -it --name auto-update-noip-client \
    -e USERNAME=${USERNAME} \
    -e PASSWORD=${PASSWORD} \
    -e HOSTNAME=${HOSTNAME} \
    -e IP=${IP} \
    -e INTERVALTIME=${INTERVALTIME}
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/noip/dynamic-update-client/index.yaml
```
- `USERNAME`:     (required)  Username login noip
- `PASSWORD`:     (required)  Password login noip
- `HOSTNAME`:     (required)  Hostname which is need to update a new ip
- `IP`:           (optional)  IP client which is mapped to hostname. If it's empty then it will be auto detected public ip
- `INTERVALTIME`: (optional)  Loop to re-update if ip is changed. 60s, 1m, 1h ... Default is no loop. [Unit time](https://github.com/circle2jt/ymlr?tab=readme-ov-file#sleep)