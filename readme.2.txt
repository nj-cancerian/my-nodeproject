After cluster setup 

#istioctl manifest install --set profile=demo
#kubectl create namespace go-demo-7
#kubectl label namespace go-demo-7 istio-injection=enabled
#kubectl --namespace go-demo-7 apply --filename k8s/istio/gateway/ recursive
#kubectl --namespace go-demo-7 rollout status deployment go-demo-7-primary #deployment of first release 

$Script to get the ip of external load balancer 
#We will make script executable  
#chmod +x k8s/istio/get-ingress-host.sh
#PROVIDER=eks
#INGRESS_HOST=$(./k8s/istio/get-ingress-host.sh $PROVIDER)
#echo $INGRESS_HOST 
#for i in {1..10}; do 
$for faking the domain of the application by injecting host header to the request 
#curl -H "Host: go-demo-7.acme.com" "http://$INGRESS_HOST/version"
#done 
#

Gateway created external load balancer <deployemt creates < replica sets < replica sets creates pods 