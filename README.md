# Try cf-mgmt

Install cf-mgmt

```shell
curl -Lo cf-mgmt https://github.com/pivotalservices/cf-mgmt/releases/download/v0.0.53/cf-mgmt-linux && chmod +x cf-mgmt && sudo mv cf-mgmt /usr/local/bin/
```

Initialize configuration

```shell
cf-mgmt init-config
```


```shell
uaac target --skip-ssl-validation uaa."$SYSTEM_DOMAIN"
uaac token client get admin -s "$CLIENT_SECRET"
uaac client add cf-mgmt \
  --name cf-mgmt \
  --secret cf-mgmt-secret \
  --authorized_grant_types client_credentials,refresh_token \
  --authorities cloud_controller.admin,scim.read,scim.write
```
