# This repository includes simple examples for every concept of Istio Service Mesh. 

## [Observability](https://github.com/Huseyinnurbaki/istio/tree/master/Observability)

*  Kiali Dashboard
*  Troubleshooting

## [Traffic Management](https://github.com/Huseyinnurbaki/istio/tree/master/TrafficManagement)




# Installation

```sh
```
# [Installation](https://istio.io/latest/docs/setup/getting-started)



```console
$ kubectl label namespace playground istio-injection=enabled
```


# Deploy Apps

```bash
$ kubectl apply -f ../yaml/common/bookinfo.yaml
$ kubectl apply -f ../yaml/common/bookinfo-gateway.yaml
```

### check if working

```bash
$ kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -s productpage:9080/productpage | grep -o "<title>.*</title>"
```




# Determining the ingress IP and ports

> ingress[0].hostname for local development (default is .ingress[0].ip)

```bash
$ export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o  jsonpath='{.status.loadBalancer.ingress[0].hostname}')

$ export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
$ export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
$ export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}')

```

# Local development Tip - Do not forget to publish port , otherwise gateway will not be accessible


```sh
$ kubectl port-forward svc/istio-ingressgateway 8080:80 -n istio-system
```



## Cheatsheet

https://istio.io/docs/tasks/traffic-management/ingress/ingress-control/#determining-the-ingress-ip-and-ports


### Change namespace

```sh
$kubectl config set-context --current --namespace=myns
```

---


### Send Multiple Requests

```sh
for i in `seq 1 100`; do curl -s -f /dev/null http://localhost/productpage; done
```

-----


### Change Profile 

$ istioctl manifest apply --set profile=demo
