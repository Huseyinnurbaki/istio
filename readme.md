# This repository includes simple examples for every concept of Isio Service Mesh. 

## [Observability](link)

*  [Kiali Dashboard](link)
*  [Troubleshooting](link)

## [Traffic Management](link)

* [Gateway](link)
* [Weighted Load Balancing](link)
* [Troubleshooting](link)

# [Policies](link)

<!-- - [Kiali Dashboard](link)
- [Troubleshooting](link) -->

# [Security](link)


## My Environment

- docker-for-desktop(mac): v2.2.0.5
- kubernetes: v1.15.5
- istioctl: v1.5.1 


# Installation

```sh
$ curl -L https://istio.io/downloadIstio | sh -
$ cd istio-1.5.1
$ export PATH=$PWD/bin:$PATH
```

```console
$ istioctl manifest apply --set profile=demo
```


>If you haven't created any certificate for your kubernetes cluster, you will see the warning below. It will not prevent discovering features of Istio.

```sh
Detected that your cluster does not support third party JWT authentication. Falling back to less secure first party JWT. See https://istio.io/docs/ops/best-practices/security/#configure-third-party-service-account-tokens for details.
```


-------
```sh
$ kubectl create ns playground
```

```sh
$ kubectl label namespace playground istio-injection=enabled
```



-------

## Cheatsheet

https://istio.io/docs/tasks/traffic-management/ingress/ingress-control/#determining-the-ingress-ip-and-ports


change ns 
$kubectl config set-context --current --namespace=myns