# Nginx Proxy with bring-your-own certificate

This is a small docker image which can be used as a reverse proxy before your
local running service. It acts as a HTTP terminating proxy.

## Usage

```bash
docker run -d --name app-roxy --net host \
  -e REMOTE_URL=http://127.0.0.1:8080 \
  -e HTTP_PORT=80 \
  -e HTTPS_PORT=443 \
  --mount type=bind,source=LOCATION_OF_CERT,target=/etc/nginx/cert.crt,readonly \
  --mount type=bind,source=LOCATION_OF_KEY,target=/etc/nginx/cert.key,readonly \
  tkafka/nginx-self-signed-https:latest
```

Note: You can pick your own values for http and https port. 
