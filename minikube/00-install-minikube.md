# Install minikube on GCP

## Create GCP instance

```sh
gcloud compute instances create minikube01 --machine-type=n1-standard-2  --boot-disk-auto-delete --image-project ubuntu-os-cloud --image ubuntu-1604-xenial-v20190306 --maintenance-policy TERMINATE --preemptible
```

## Install minikube

```sh
sudo apt-get update
sudo apt-get install     apt-transport-https     ca-certificates     curl     gnupg-agent     software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
b_release -cs) \
le"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker ps
sudo chgrp gavin /var/run/docker.sock
docker ps
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64   && chmod +x minikube
sudo cp minikube /usr/local/bin && rm minikube

export CHANGE_MINIKUBE_NONE_USER=true
sudo minikube start --vm-driver=none
sudo iptables -P FORWARD ACCEPT
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
kubectl get no
sudo mv /home/gavin/.kube /home/gavin/.minikube $HOME
sudo chown -R $USER $HOME/.kube $HOME/.minikube
kubectl get no
```
