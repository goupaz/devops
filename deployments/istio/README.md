Reference: https://istio.io/latest/docs/setup/install/helm/


helm repo add istio https://istio-release.storage.googleapis.com/charts
helm repo update

kubectl create namespace istio-system

helm install istio-base istio/base -n istio-system
helm install istiod istio/istiod -n istio-system --wait

kubectl create namespace istio-ingress
kubectl label namespace istio-ingress istio-injection=enabled
kubectl label namespace default istio-injection=enabled
helm install istio-ingress istio/gateway -n istio-ingress --wait
