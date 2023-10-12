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
