# Copy SSL certificates

In CEDAR development `Nginx` communicates with the browser over `https`.
You will need to add the previously generated self signed certificates to `nginx`.

```sh
sudo mkdir -p /etc/nginx/cedar/ssl
cp ${CEDAR_HOME}/CEDAR_CA/cedar.metadatacenter.orgx.crt \
  /etc/nginx/cedar/ssl/ 
cp ${CEDAR_HOME}/CEDAR_CA/cedar.metadatacenter.orgx.key \
  /etc/nginx/cedar/ssl/
```
