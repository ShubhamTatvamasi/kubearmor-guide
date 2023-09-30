# Vault

Start Minikube cluster: 
```bash
minikube start
```

Deploy Vault:
```bash
helm install vault hashicorp/vault
```

Check if Vault server is ready:
```bash
kubectl get pods
```

Port-forward vault service:
```bash
kubectl port-forward service/vault 8200:8200
```

http://localhost:8200/ui/


Get the vault token to unlock Vault:
```bash
bat vault-cluster-vault-2023-09-30T15_28_11.909Z.json
```

Get inside Vault pod:
```bash
kubectl exec -it vault-0 -- sh
```

Go to Vault data directory:
```bash
cd /vault/data
```

Delete minikube cluster:
```bash
minikube delete
```
