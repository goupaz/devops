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

openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -subj '/O=GOUP Inc./CN=goupaz.com' -keyout goupaz.com.key -out devops.goupaz.com.crt

openssl req -out devops.goupaz.com.csr -newkey rsa:2048 -nodes -keyout devops.goupaz.com.key -subj "/CN=devops.goupaz.com/O=goupaz organization"

openssl x509 -req -days 365 -CA devops.goupaz.com.crt -CAkey goupaz.com.key -set_serial 0 -in devops.goupaz.com.csr -out devops.goupaz.com.crt

kubectl create -n istio-ingress secret tls helloworld-credential --key=devops.goupaz.com.key --cert=devops.goupaz.com.crt


kubectl -n istio-ingress get service istio-ingress