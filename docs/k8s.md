# Preprequisistes

- Helm 3
- Kubectl client 1.18
- Terraform 1.12.7 


# Steps

1. Install Kubernetes via terraform in GKE:
```
cd infrastructure/terraform/environments/production/gcp/accounts/prod1/regions/us-central1
terraform init
terraform plan -out 1.tfplan
terraform apply -f 1.tfplan
```

2. Install NGINX via Helm:
```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
kubectl create ns management
helm install nginx ingress-nginx/ingress-nginx --namespace management
```
3. Install Wordpress and Mysql located in /applications/wordpress folder:

```
kubectl apply -k .
```

4. Install Redis in located in /applications/redis folder:
```
kubectl apply -k .
```

