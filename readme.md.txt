Repo used = https://github.com/nj-cancerian/Calculator
1-Created jenkins server on Ec2 
2-On jenkins server installed maven plugin and confifured under the global settings 
3-Created a job A. SCM checkout B. Maven clean package Link for the -Url 3.111.32.156:8080/job/my-proeject/
4-Once job is created moved to another ec2 machine on which docker is installed by using transfer.sh script 
5-Run the docker build command to build the image docker build -t nitjoshi/app:update .
6- Use docker loging and then docker push command to push the image to docker central repo docker push nitjoshi/app:update
8-Now used main.tf file to build the eks environement 


#################################INSTALLING KUBECTL COMMAND ON LOCAL LINUX MACHINE ############################################

Kink used =  https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --checkc
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client

############################# to configure eks cluster ###########################################

For configuring of the eks server in your local 
aws eks update-kubeconfig --name test-eks --region ap-south-1


######################## Permission required for iam to manage the cluster 
Under iam role < select user < add inline policy 
Service type EKS
Actions = all # including read , write and review 
Resources = all resources 
Permission required 




################################## To resolve cluster access issue ##############
Document followed = https://aws.amazon.com/premiumsupport/knowledge-center/eks-api-server-unauthorized-error/ 


$$$$$$$$$$$$$$$$$$$$$$$ added one $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
istioctl profile dump demo #will show the istio profile as we are using demo profile 


1)#Installing istio by using profile demo
istioctl install --set profile=demo -y 

To verify we will use custom resource defination and we are only willing to get the istio services *istio.io
kubectl get crds | grep "istio.io" #to check the istio services 
kubectl --namespace istio-system get pods #will give all the istio services 

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
-->Manual side car injection to istio 

injecting side car proxy into the istio services 
istioctl kube-inject --filename <sample>.yml
istioctl kube-inject --filename <sample>.yml | kubectl apply --filename -

Automatic proxy injection 
##
kubectl label namespace default istio-injection=enabled

To check whethere automatic side car injection policy is enabled 
kubectl describe namespace default 
kubectl rollout restart deployment <label name > #this will redeploy the pods with the side card proxy   
kubectl describe pod --selector app=<label name >

if we want to disable the autoinjecton of side car proxy 
kubectl label namespace default istio-injection-
Kubectl rollout restart deployement <label name >








$$$$$$$$$$$$$$$ TO DElETE ISTIO FROM YOUR K8S CLUSTER $$$$$$$$$
istioctl manifest generate --set profile=demo | kubectl delete --filename -