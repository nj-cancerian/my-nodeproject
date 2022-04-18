# nodeapp
Git URL =https://github.com/nj-cancerian/my-nodeproject.git
created an ec2 and installed docker using the docker script from docker hub and java 11 using the apt distributgor 
Configured agent node on the jenkins server .
Under the security group for the agent allowed tcp port 50000 for jenkins worker connection 
Installed jenkins agent using java -jar agent.jar
Downloaded and started the jenkins agent on worker node and provide pat /opt/build
Configured docker hub token and git token under the jenkins file 
Created docker file for node installation "note we have exposed our app on port on 3000" 
Created jenkins file (it will chgeckout , then build docker image using the docker file , login to docker hub and push image to docker hub , then  logout )





#################################### creating aws eks using the terraform file ##################################################
created terraform main file withg variable .tf 
terraform init -backend-config="access_key=<key>" -backend-config="secret_key=<key>"
terrraform plan #for dry run
Terraform apply  



[eksctl create cluster --name tp-cluster-1 --nodes 2 --node-type t2.micro --managed --region us-east-1        #another approach
]


####################################            ISTIO SERVICE MESH             #################################################
Websitge used https://istio.io/latest/docs/setup/getting-started/
download istgio by using curl -L https://istio.io/downloadIstio | sh -
mv -v istio-1.13.2 /opt/
export PATH="$PATH:/opt/istio-1.13.2/bin" # export spath for istio 
