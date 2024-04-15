# portainer webhook-stack
Webhook to auto pull and redeploy a stack in portainer ce

## Run in a docker
#### Run with an access token
```sh
  docker run --rm -it --name portainer-webhook \
    -e url=${PORTAINER_URL} \
    -e token=${PORTAINER_TOKEN} \
    -e name=${ENVIRONMENT_NAME}/${STACK_NAME} \
    -e pullImage=${PULLIMAGE} \
    -e prune=${PRUNE} \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/portainer/webhook-stack/index.yaml
```
- `PORTAINER_URL`:      the portainer url
- `PORTAINER_TOKEN`:    user access token in the portainer
- `ENVIRONMENT_NAME`:   environment name in portainer and 
- `STACK_NAME`:         stack name
- `PULLIMAGE`:          repull image and redeploy (`true`/`false`. Default is `true`)
- `PRUNE`:              auto prune (`true`/`false`. Default is `false`)


#### Run with username/password
```sh
  docker run --rm -it --name portainer-webhook \
    -e url=${PORTAINER_URL} \
    -e username=${PORTAINER_USER} \
    -e password=${PORTAINER_PASS} \
    -e name=${ENVIRONMENT_NAME}/${STACK_NAME} \
    -e pullImage=${PULLIMAGE} \
    -e prune=${PRUNE} \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/portainer/webhook-stack/index.yaml
```
- `PORTAINER_URL`:      the portainer url
- `PORTAINER_USER`:     username in the portainer
- `PORTAINER_PASS`:     password for username in the 
- `ENVIRONMENT_NAME`:   environment name in portainer and 
- `STACK_NAME`:         stack name
- `PULLIMAGE`:          repull image and redeploy (`true`/`false`. Default is `true`)
- `PRUNE`:              auto prune (`true`/`false`. Default is `false`)
