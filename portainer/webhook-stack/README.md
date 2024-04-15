# portainer webhook-stack
Webhook to auto pull and redeploy a stack in portainer ce

## Run in a docker
```sh
  docker run --rm -it --name portainer-webhook \
    -e url=${PORTAINER_URL} \
    -e username=${PORTAINER_USER} \
    -e password=${PORTAINER_PASS} \
    -e name=${ENVIRONMENT_NAME}/${STACK_NAME} \
    -e pullImage=true \
    -e prune=false \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/portainer/webhook-stack/index.yaml

  # PORTAINER_URL:      the portainer url
  # PORTAINER_USER:     username in the portainer
  # PORTAINER_PASS:     password for username in the 
  # ENVIRONMENT_NAME:   environment name in portainer and 
  # STACK_NAME:         stack name
  # pullImage:          repull image and redeploy
  # prune:              auto prune
```
