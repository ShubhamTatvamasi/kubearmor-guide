# kubearmor-guide

Create nginx deployment:
```bash
kubectl create deployment nginx --image=nginx
```

Expose nginx:
```bash
kubectl expose deployment nginx --port 80 --type LoadBalancer
```

Test connection:
```bash
curl 192.168.1.220
```

Check the live activities:
```bash
karmor profile -n default
```

Test again:
```bash
curl 192.168.1.220
```

Get shell access for the pod:
```bash
kubectl exec -it deploy/nginx -- bash
```

Install nginx web policy:
```bash
kubectl apply -f - << EOF
apiVersion: security.kubearmor.com/v1
kind: KubeArmorPolicy
metadata:
  name: nginx-webpage-block
spec:
  severity: 10
  selector:
    matchLabels:
      app: nginx
  file:
    matchPaths:
    - path: /usr/share/nginx/html/index.html
      fromSource:
      - path: /usr/sbin/nginx
      action: Allow
    - path: /usr/share/nginx/html/index.html
      action: Block
EOF
```

Delete Nginx:
```bash
kubectl delete deployment nginx
kubectl delete svc nginx
```

Delete policy:
```bash
kubectl delete kubearmorpolicy nginx-webpage-block
```

