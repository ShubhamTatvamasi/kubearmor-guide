# karmor

We will be using `karmor` cli tool for managing our KubeArmor operator

Download karmor:
```bash
curl -sfL http://get.kubearmor.io/ | sudo sh -s -- -b /usr/local/bin v0.14.1
```
> `v0.14.1` is the last version to support `karmor discover` and `karmor summary`

Get the list of all the supported sub-commands:
```bash
karmor
```

This is tell us if KubeArmor is currently installed on our cluster or not:
```bash
karmor version
```

Install KubeArmor to cluster:
```bash
karmor install
```

Probe will give us detailed information our cluster and active LSM: 
```bash
karmor probe
```

profile will give us live metrices of Process, File, Network and Syscall:
```bash
karmor profile -n default
```

logs will give us realtime alerts:
```bash
karmor logs
```

Delete KubeArmor from cluster:
```bash
karmor uninstall
```

---

Let's also install discovery-engine:
```bash
kubectl apply -f https://raw.githubusercontent.com/accuknox/discovery-engine/dev/deployments/k8s/deployment.yaml
```

Get the recommendations for our running pods:
```bash
karmor recommend
```
> this will generate default policies for our deployments to `~/out` folder.


```bash
cat hashicorp-vault-k8s-1-2-1-write-under-bin-dir.yaml
```



