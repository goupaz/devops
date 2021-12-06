Reference: https://goteleport.com/docs/kubernetes-access/getting-started/cluster/

helm repo add teleport https://charts.releases.teleport.dev

helm install teleport-cluster teleport/teleport-cluster --create-namespace --namespace=teleport-cluster \  --set clusterName=${CLUSTER_NAME?} --set acme=true --set acmeEmail=${EMAIL?}