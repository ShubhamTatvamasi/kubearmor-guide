# kubearmor-guide

Create nginx deployment:
```bash
kubectl create deployment nginx --image=nginx
```

Expose nginx:
```bash
kubectl expose deployment nginx --port 80 --type LoadBalancer
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
