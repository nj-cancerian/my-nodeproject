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
#cat k8s/istio/split/exercise/app-0-0-2-g.yaml
#diff k8s/istio/gateway/app/deployment.yaml k8s/istio/split/exercise/app-0-0-2-g.yaml
#kubectl --namespace go-demo-7 apply --filename k8s/istio/split/exercise/app-0-0-2-g.yaml
#kubectl --namespace go-demo-7 rollout status deployment go-demo-7-bg
#for i in {1..100}; do
#curl -H "Host: go-demo-7.acme.com" "http://$INGRESS_HOST/version"
#done

#kubectl --namespace go-demo-7 get deployments

#kubectl --namespace go-demo-7 describe service go-demo-7

#kubectl --namespace go-demo-7 describe virtualservice go-demo-7

#kubectl --namespace go-demo-7 describe gateway go-demo-7

#Gateway created external load balancer <deployemt creates < replica sets < replica sets creates pods 