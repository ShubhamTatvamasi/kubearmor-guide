# kubearmor-guide

Create nginx deployment:
```bash
kubectl create deployment nginx --image=nginx
```

Get shell access for the pod:
```bash
kubectl exec -it deploy/nginx -- bash
```
