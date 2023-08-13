# patch


```
kubectl -n kube-system patch ds kubearmor \
  --type='json' \
  --patch='[{
    "op": "replace",
    "path": "/spec/template/spec/containers/0/resources",
    "value": {
      "requests": {
        "memory": "200Mi",
        "cpu": "250m"
      },
      "limits": {
        "memory": "300Mi",
        "cpu": "500m"
      }
    }
  }]'
```
