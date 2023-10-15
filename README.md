## Hagital Cloud Engineer Program Git-Class-Lesson-101  
## Download git bash  
- https://git-scm.com/downloads  
## Configure Git Bash  
- git config --global user.name "Jones"
- git config --global user.email "jonesarchibong@gmail.com"
## Prepare Working Environment  
- mkdir website "This command help to create a directory"
- cd website "This command is used to enter a directory"
- git init "This command is used to initialize"
- touch index.html "This command is used to create html file"
- vim index.html "This command is used to edit html file"
- :wq "Save the file and exit"
## Clone your Repo
- git remote add origin (url) "This is the url from the Project Repo"
## Push to github  
- git add index.html
- git commit -m "add a note"
- git push origin master

## KUBERNETES
## Run your VMware
- VMware or through SSH can be used.
- sudo su [be on the root]
- apt-get update [run update on your vmware]
- apt-get upgrade [upgrade your Vmware]
## VIRTUALBOX - Install
- sudo apt install virtualbox virtualbox-dkms virtualbox-qt virtualbox-ext-pack [install virtualbox]
## DOCKER - Install
- Step 1: # Add Docker's official GPG key: sudo apt-get update sudo apt-get install ca-certificates curl gnupg sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg sudo chmod a+r /etc/apt/keyrings/docker.gpg # Add the repository to Apt sources: echo \ "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \ "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \ sudo tee /etc/apt/sources.list.d/docker.list > /dev/null sudo apt-get update
- Step 2: sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
- docker - - version [confirm the Docker version]
- systemctl enable docker [enable Docker]
- systemctl start docker [start the Docker]
- systemctl status docker [confirm Docker status]
- sudo usermod -aG docker $USER && newgrp docker
## MINIKUBE - Download and Install
- wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 
chmod +x minikube-linux-amd64 
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
- minikube version [confirm minikube version]
## KUBECTL ON UBUNTU
- curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
- chmod +x ./kubectl [change mode]
- sudo mv ./kubectl /usr/local/bin/kubectl
- Verify kubectl [to verify your kubernetes]
- kubectl version -o json --client [confirm kubenertes version]
- minikube start --driver=docker [start the kubernetes]
- sudo usermod -aG docker $USER && newgrp docker
- kubectl get nodes
- kubectl create deployment jones –image=nginx [you need to specify the name of your deployment and image [ubuntu, nginx, redis, tomcat etc]
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube addons enable metric-server
- Kubectl expose deployment jones --type=NodePort --port=8080 [enable port 8080]
- Kubectl get service
- Kubectl describe service
- Kubectl describe deployment
- Kubectl delete service jones
- Kubectl delete deployment jones
- Minikube stop
## PODS - KUBERNETES
- mkdir kandyjonesk8s-pods
- cd kandyjonesk8s-pods
- minikube start --driver=docker
- kubectl run kandyjonesk8s-pods --image=redis
- kubectl get pods
- kubectl get pod kandyjonesk8s-pods -o yaml
- kubectl describe pod kandyjonesk8s-pods
- kubectl run pyidyjok8s-pods --image=nginx --dry-run=client -o yaml > kandyjones.yaml [create another pods as sidecar]
- cat kandyjones.yaml
- vim kandyjones.yaml [use vim to edit the yaml file. create another image and file name for a sidecar] :wq to save
- kubectl apply -f kandyjones.yaml
## PODS DEPLOYMENT - KUBERNETES
- kubectl create deployment kandyjonesk8s-dep --image=ubuntu
- kubectl edit deployment kandyjonesk8s-dep
- kubectl get deployment kandyjonesk8s-dep
- kubectl delete deployment kandyjonesk8s-dep
- kubectl create depolyment pyidyjok8s-dep --image=nginx
- kubectl scale deployment pyidyjok8s-dep --replicas=12
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube addons enable metrics-server [run minikube addons]
- minikube dashboard [confirm your deployment. deployment will be launched on your default browser. Check your browser]
- minikube stop 
