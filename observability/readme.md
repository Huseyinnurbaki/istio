
## Index

* [Kiali](#kiali)
* [Troubleshooting](#troubleshooting)

## Go to ./yaml folder

# Kiali

```sh
$kubectl -f kialisecret.yaml apply
```

* Username: admin

* Password: admin

> username & passphrase values are base64 encoded. For this tutorial, username & passpharase values are same. (YWRtaW4=) which is admin


## Enable Kiali

```
kubectl apply -f samples/addons
kubectl rollout status deployment/kiali -n istio-system
```