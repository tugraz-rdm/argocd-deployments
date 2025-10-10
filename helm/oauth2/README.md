# oauth2-proxy

Quick OAuth2 proxy through Keycloak OIDC setup with Helm charts based on https://github.com/oauth2-proxy.

## Config

The values now are set to enable an authentication through Keycloak-OIDC. This needs: **clientID, clientSecret, oidcIssuerURL**.

Because oauth2-proxy is deployed as a different namespace in a k8s cluster, **upstream** parameter needs to also be set. This should point to the ingress of your service that is proxied by OAuth2.

## Usage

Clone this repository. Edit the placeholders in _values.yaml_ to the ones according to your service.

Then run these commands:

```
helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests
helm repo update
helm install oath2-proxy oauth2-proxy/oauth2-proxy
```

- To install a new oauth2-proxy namespace:

```
helm install oauth2-proxy oauth2-proxy/oauth2-proxy   --namespace oauth2-proxy   --create-namespace   -f values.yaml
```

- To update the chart:

```
helm upgrade oauth2-proxy oauth2-proxy/oauth2-proxy   --namespace oauth2-proxy   -f values.yaml
```

More details: https://github.com/oauth2-proxy/manifests/tree/main/helm/oauth2-proxy


- Example annotation for the targeted service ingress:
```
ingress:
  annotations:
    nginx.ingress.kubernetes.io/auth-url: "https://<Domain>/oauth2/auth"
    nginx.ingress.kubernetes.io/auth-signin: "https://<Domain>/oauth2/start?rd=https://$host$request_uri"
    nginx.ingress.kubernetes.io/auth-response-headers: "X-Auth-Request-Email,X-Auth-Request-User"
```
