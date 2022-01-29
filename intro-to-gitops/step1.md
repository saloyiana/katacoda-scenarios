Task: 
1. Namespace Creation 
In this step, we will install argocd.
First, we need to create argocd namespace by running this command:
kubectl create namespace argocd{{execute}}

2. Argocd Installation 
Now, we will install argocd using its offcial helmchart: 
helm repo add argo https://argoproj.github.io/argo-helm  && helm repo update && helm install argocd argo/argo-cd -n argocd{{execute}}

3. Argocd UI Access 
To access argocd UI, we can use port-forward command:
In a new terminal, run 
kubectl port-forward svc/argocd-server -n argocd 8080:443{{execute}}
Open a new select port tap and enter the port 8080 

4. Argocd Creds
UserName: Admin
Password: To get the Argocd password:
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo{{execute}}



