# Running kubernetes on windows

The easiest way to run kube on windows is to use Docker for Windows and enable the Kubernetes flag.

This will create a single local cluster.

To add the web ui you can use these commands

1. Add the ui


```sh
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta6/aio/deploy/recommended.yaml
```

2. Proxy the ui

```sh
kubectl proxy
```

Then access it on [http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy](http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy)

