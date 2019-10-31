The installation of components has been taken care in below order.

1.  Docker Installation
	sudo apt-get install docker-ce docker-ce-cli containerd.io

2.  VirtualBox Installation
	sudo apt-get install virtualbox
	
3. kubectl Installation
	curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/OS_DISTRIBUTION/amd64/kubectl
	chmod +x ./kubectl
	sudo mv ./kubectl /usr/local/bin/kubectl

4. minikube Installation
	curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
	sudo mkdir -p /usr/local/bin/
	sudo install minikube /usr/local/bin/

5. Helm & tiller Installation
	curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
	chmod 700 get_helm.sh
	./get_helm.sh
	kubectl create serviceaccount -n kube-system tiller
	kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
	helm init --service-account tiller

6. Jenkins Installation
	docker run \
	-u root \
	--rm \
	-d \
	-p 8080:8080 \
	-p 50000:50000 \
	-v jenkins-data:/var/jenkins_home \
	-v /var/run/docker.sock:/var/run/docker.sock \
	jenkinsci/blueocean

And the output of installation is given in the images