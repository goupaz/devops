# Devops

## Task

- Write a pipeline that will deploy an "hello world" web app to Kubernetes
- The CI/CD system (where the pipeline resides) and the Kubernetes cluster should be on separate systems
- The web app should be accessible remotely and only with HTTPS

## Requirements

- The submission (code/scripts) must be checked into a repository (eg. Github, Gitlab, BitBucket etc.) 
- The submission must include clear instructions to run the code/scripts/commands to produce the setup. 
- No restriction on the tool/framework/programming language. 
- No restriction on use of any of the public clouds - GCP/AWS/Azure. 
- No restriction on use of any open source tools or libraries. 
- Explain in detail how these libraries/tools work internally. If you are unsure about their internals, it is better to avoid using them and go with a simpler, more understandable approach instead.

## Goal
- The assignment is open ended and the point of the exercise is to assess code modularity, usability, extensibility and debuggability. 
- Working solution with scope/ideas for improvement and their pros/cons which will be discussed in a follow up meeting.

Tooling
- Teleport
- Cert-manager
- Istio
- Meshery
- Dockerhub
- Terraform-cloud
- GithubAction - CI
- ArgoCD - CD
- Harbor - Push/Pull
- Monitoring - Istio ones
  - Zipkin / Jaeger
  - Grafana
  - Prometheus
  - Kiali
  - Meshery
- Helmfile / helm
- Autoscaler
  - [karpenter](https://github.com/aws/karpenter) 
- Vault/Console

## Steps
1. Bring cluster up in EKS:
```
cd infrastructure/terraform/environments/production/aws/accounts/aws_prod01/regions/us-east-1/compute/eks
terraform init
terraform plan
terraformapply 
```
2. Add cluster to kubeconfig:
```
aws eks update-kubeconfig --name master-UE9fmXo5 --profile AdministratorAccess-645358331312
```

3.
