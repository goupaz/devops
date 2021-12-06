Reference: https://argo-cd.readthedocs.io/en/stable/getting_started/

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```
brew install argocd
```

The initial password for the admin account is auto-generated and stored as clear text in the field password in a secret named argocd-initial-admin-secret:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

ArgoCD UI:
```
kubectl port-forward svc/argocd-server -n argocd 8080:443 &
```

Update pwd:
```
argocd login 127.0.0.1:8080
argocd account update-password
```

Add cluster:
```
argocd cluster add arn:aws:eks:us-east-1:645358331312:cluster/master-UE9fmXo5
```
