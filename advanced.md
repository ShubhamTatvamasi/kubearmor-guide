# Advanced

recommend will download the docker images for your deployments and give me kubearmor recommended policies to apply:
```bash
karmor recommend -n default
```

Go to the recommend policies directory:
```bash
cd ~/out/default-nginx
```

This policy will block the package management execution:
```bash
head -n 20 nginx-latest-pkg-mngr-exec.yaml
```

First get inside pod:
```bash
kubectl exec -it deploy/nginx -- bash
```

Check apt command:
```bash
apt update
```

Apply policy:
```bash
kubectl apply -f nginx-latest-pkg-mngr-exec.yaml
```

Check apt command again:
```bash
apt update
```

