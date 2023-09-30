# karmor

We will be using `karmor` cli tool for managing our KubeArmor operator

Download karmor:
```bash
curl -sfL http://get.kubearmor.io/ | sudo sh -s -- -b /usr/local/bin
```

Install KubeArmor to cluster:
```bash
karmor install
```

Check kubearmor status:
```bash
kubectl get po -A -l kubearmor-app
```

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


Checks for supported KubeArmor features in the current environment:
```bash
karmor probe
```

---

This will install 3 pods to our cluster:
```
kubearmor - 
kubearmor-controller - 
kubearmor-relay - 
```

