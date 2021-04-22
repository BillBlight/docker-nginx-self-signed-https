# Nginx Proxy with bring-your-own certificate

This is a small docker image which can be used as a reverse proxy before your
local running service. It acts as a HTTP terminating proxy.

This was originally forked from tkafka/docker-nginx-self-signed-https.
I made a couple changes to it after forking it.

## Usage

```bash
docker run -d --name app-roxy --net host \
  -e REMOTE_URL=http://127.0.0.1:8080 \
  -e HTTP_PORT=80 \
  -e HTTPS_PORT=443 \
  -e SERVER_NAME=localhost \
  --mount type=bind,source=HOST_LOCATION_OF_CERT,target=/certs/cert.crt,readonly \
  --mount type=bind,source=HOST_LOCATION_OF_KEY,target=/certs/cert.key,readonly \
  ghcr.io/billblight/simple-nginx-https-proxy:latest
```

Note: You can pick your own values for http and https port. 
