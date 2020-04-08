
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

```sh
$istioctl manifest apply --set values.kiali.enabled=true
```

## Apply Bookinfo Yaml

```sh
$kubectl -f bookinfo.yaml apply
```
## Apply Bookinfo Gateway Yaml

```sh
$kubectl -f bookinfo-gateway.yaml apply
```

## Start Kiali Dashboard

```sh
$istioctl dashboard kiali
```


# Troubleshooting

```sh
$istioctl manifest apply --set profile=demo
```

```sh
$kubectl label namespace playground istio-injection=enabled
```


## cleanup


```sh
$kubectl -f bookinfo.yaml delete
```
```sh
$kubectl -f bookinfo-gateway.yaml delete
```