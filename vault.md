# Vault

Create a minikube cluster:
```bash
multipass launch minikube
```

Get inside minikube vm:
```bash
multipass shell minikube
```

Install Helm
```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

Add hashicorp repo:
```bash
helm repo add hashicorp https://helm.releases.hashicorp.com
```

Deploy Vault:
```bash
helm install vault hashicorp/vault \
  --create-namespace \
  --namespace vault \
  --set ui.serviceType=LoadBalancer
```

Check if Vault server is ready:
```bash
kubectl -n vault get pods
```

Port-forward vault service:
```bash
kubectl -n vault port-forward --address 0.0.0.0 service/vault 8200:8200
```

Get the VM IP:
```bash
multipass ls
```

http://192.168.64.6:8200/ui/


Get the vault token to unlock Vault:
```bash
bat vault-cluster-vault-2023-09-30T15_28_11.909Z.json
```

Get inside Vault pod:
```bash
kubectl -n vault exec -it vault-0 -- sh
```

Go to Vault data directory:
```bash
cd /vault/data
```

Delete minikube cluster:
```bash
multipass delete minikube --purge
```

