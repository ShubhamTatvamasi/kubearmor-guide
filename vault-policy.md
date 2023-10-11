# Vault Policy

Create Vault policy:
```yaml
kubectl apply -f - << EOF
apiVersion: security.kubearmor.com/v1
kind: KubeArmorPolicy
metadata:
  name: ksp-vault-protect
  namespace: vault
spec:
  action: Allow
  severity: 10
  selector:
    matchLabels:
      app.kubernetes.io/instance: vault
      component: server
  file:
    matchDirectories:
      - dir: /vault/
        recursive: true
        action: Block
      - dir: /
        recursive: true
      - dir: /vault/
        recursive: true
        fromSource:
          - path: /bin/vault
  process:
    matchPaths:
    - path: /bin/busybox
    - path: /bin/vault
EOF
```
