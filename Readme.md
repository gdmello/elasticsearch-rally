Summary
=======
Helm chart to run the official Elasticsearch performance verification tool - rally as a pod.

Usage
=====
```
$ helm install --name esrally -f elasticsearch-rally/values.yaml elasticsearch-rally --namespace ft
NAME:   esrally
LAST DEPLOYED: Fri Nov  3 17:23:53 2017
NAMESPACE: ft
STATUS: DEPLOYED

RESOURCES:
==> v1beta1/Deployment
NAME          DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
k8s-es-rally  1        1        1           0          0s

```

