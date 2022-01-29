In this step, we will install argocd.   

First, we need to create argocd namespace by running this command:   
`kubectl create namespace argocd`{{execute}}
if you see this error:
`The connection to the server localhost:8080 was refused - did you specify the right host or port?`, then run `minikube status`{{execute}} to check the kubernetes cluster status, wait until the output shows: 
```
host: Running
kubelet: Running
apiserver: Stopped
kubeconfig: Configure
```
then try to create the namespace again. 

### Helm Installation: 
Helm is a package manager that helps you to find, share, and use software that is built for Kubernetes. Helm streamlines the installation and management of Kubernetes applications, and is the equivalent of the apt, yum, or homebrew utilities for Kubernetes. In this tutorial we will use helm to install Argocd.

 `wget https://get.helm.sh/helm-v3.8.0-linux-amd64.tar.gz && tar -xf helm-v3.8.0-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/`{{execute}} 

To verify your installation, run `helm version`{{execute}}, the output should be something like: ```version.BuildInfo{Version:"v3.8.0", GitCommit:"d14138609b01886f544b2025f5000351c9eb092e", GitTreeState:"clean", GoVersion:"go1.17.5"}``` 
### Argocd Installation:
After installing helm, we will install argocd using its official helm chart:

`helm repo add argo https://argoproj.github.io/argo-helm  && helm repo update && helm install argocd argo/argo-cd -n argocd`{{execute}}

### Argocd UI:
To access argocd UI, we can use `port-forward` command:   
In a new terminal, run `kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0`{{execute}}
   
Click on the plus icon (+), then click on select a `port to view on host1` and enter the port `8080`

### Argocd Login:
To login into Argocd: 
```
Username: admin
and to get the argocd password, run:
```
`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`{{execute}}



