
## Index

* [Gateway](#gateway)
* [Weighted Load Balancing](#weighted-load-balancing)
* [Troubleshooting](#troubleshooting)

## Go to ./yaml folder

# Gateway 

```console
$ kubectl -f  gateway.yaml  apply
```

# Weighted Load Balancing

```console
$ kubectl -f wlb.yaml  apply
```
# Troubleshooting

>Make sure you have enabled sidecar injection in your namespace

Easy way to check if you have enabled sidecar injection is to list pods that you just created with command:

```console
$ kubectl get po -n 
```
If you are seeing 1/1 under ready title, this means you don't have sidecars inside your pods.

Correct output:

```console
NAME                      READY   STATUS    RESTARTS   AGE
whoami-544c5fdb99-whs4s   2/2     Running   0          96m
```

Delete what you've created. 

```console
kubectl -f  gateway.yaml  delete
```

Enable sidecar injection.

```console
$ kubectl label namespace playground istio-injection=enabled
```
