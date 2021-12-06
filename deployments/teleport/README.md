Reference: https://goteleport.com/docs/kubernetes-access/getting-started/cluster/

helm repo add teleport https://charts.releases.teleport.dev

helm install teleport-cluster teleport/teleport-cluster --create-namespace --namespace=teleport-cluster --set clusterName=teleport.goupaz.com --set acme=true --set acmeEmail=goupaz.team@gmail.com

MYIP=$(kubectl get services teleport-cluster -o jsonpath='{.status.loadBalancer.ingress[0].ip}')


```
POD=$(kubectl get pod -l app=teleport-cluster -o jsonpath='{.items[0].metadata.name}' -n teleport-cluster)

kubectl exec -i ${POD} -n teleport-cluster -- tctl create -f < member.yaml 
kubectl exec -ti ${POD} -n teleport-cluster -- tctl  users add sako --roles=member
kubectl exec -i ${POD} -n teleport-cluster -- tctl get role/sako
export KUBECONFIG=teleport-kubeconfig.yaml
KUBECONFIG=teleport-kubeconfig.yaml tsh login --proxy=teleport.goupaz.com:443 --user=sako

```