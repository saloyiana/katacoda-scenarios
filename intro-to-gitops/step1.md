In this step, we will install argocd.   

First, we need to create argocd namespace by running this command:   
`kubectl create namespace argocd`{{execute}}
if you see this error `The connection to the server localhost:8080 was refused - did you specify the right host or port?`, then run `minikube status`{{execute}} to check the kubernetes cluster status, wait until the output shows: 
```
host: Running
kubelet: Running
apiserver: Stopped
kubeconfig: Configure
```
then try to create the namespace again. 

After that we will install argocd using its offcial helmchart:   
`helm repo add argo https://argoproj.github.io/argo-helm  && helm repo update && helm install argocd argo/argo-cd -n argocd`{{execute}}

`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`{{execute}} 

To access argocd UI, we can use port-forward command:   
In a new terminal, run `kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0`{{execute}}
   
Click on the plus icon (+), then click on select a port to view on host1 and enter the port 8080 
or click on https://2886795274-8080-simba09b.environments.katacoda.com/

To login into Argocd, use admin as UserName, and to get the argocd password, run   
`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`{{execute}}



