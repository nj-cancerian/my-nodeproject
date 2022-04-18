# nodeapp
Git URL =https://github.com/nj-cancerian/my-nodeproject.git
created an ec2 and installed docker using the docker script from docker hub and java 11 using the apt distributgor 
Configured agent node on the jenkins server .
Under the security group for the agent allowed tcp port 50000 for jenkins worker connection 
Installed jenkins agent using java -jar agent.jar
Downloaded and started the jenkins agent on worker node and provide pat /opt/build
Configured docker hub token and git token under the jenkins file 
Created docker file for node installation "note we have exposed our app on port on 3000" 
Created jenkins file 