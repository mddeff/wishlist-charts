# Wishlist Helm Chart
This helm chart installs the [Wishlist web application](https://github.com/cmintey/wishlist) written by [cmintey](https://github.com/cmintey/).  This is an **unofficial chart** utilizing the official docker image. 

Please submit any *application* or container image issues with the upstream repository.  

Please do not submit any issues with the helm chart to the upstream repo as it is unofficial and unsupported.


## Using this chart
```bash
helm repo add wishlist https://mddeff.github.io/wishlist-charts/
helm repo update
# make values-local.yaml locally from overrides of charts/wishlist/values.yaml 
helm upgrade --install my-cool-wishlist-release wishlist/wishlist --namespace wishlist --create-namespace -f values-local.yaml
```


## example wishlist overrides
Defaults are an attempt at sanity. Only thing you will want to override is your ingress info.  Heres an example for using traefik:

```yaml
ingress:
  enabled: true
  # labels: {}
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: websecure
    traefik.ingress.kubernetes.io/router.tls.certresolver: internalacme
  host: "wishlist.example.com"
  path: "/"
  tls:
    - hosts:
      - wishlist.example.com
      # secretName: 
```

> Note that in the example above, `websecure` and `internalacme` are dependent on my traefik config. YMMV. [RTFM](https://doc.traefik.io/traefik/). All that good stuff. 

## Warranty
TL;DR - Caveat Emptor. There is no warranty express or implied of fitness for a particular purpose.