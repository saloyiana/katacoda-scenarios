## Argocd Source Configration.
### GitHub Account 
1. fork `https://github.com/argoproj/argocd-example-apps.git` to your account. 

2. In the `guestbook` folder, open `guestbook-ui-deployment.yaml`, and change the image version to `gcr.io/heptio-images/ks-guestbook-demo:0.1` instead of `gcr.io/heptio-images/ks-guestbook-demo:0.2`

Open Argocd UI, From the `admin` page, click on `repositories`, `connect using https`, then enter the source url (e.g., https://github.com/<username>/argocd-example-apps).

# Argocd Applcation Creation
First we need to create the application namespace (e.g., let's call it `demo`)

`kubectl create namespace demo`{{execute}}

Open Argocd UI, then click on `add new app`, enter the details as follows: 
```
application name: demo
project: default
sync policy: manual
Source: 
- repo: from the drop-down list, select the configured source,
- branch: HEAD
- path: guestbook.

Destination:
- cluster: in-cluster 
- namespace: demo, 
```
then click on `create`.
 
Wait until the application status shows `healthy`, then try to access it by running this command in a new terminal: 
`kubectl port-forward svc/guestbook-ui -n demo 3333:80 --address 0.0.0.0`{{execute}}

Click on the plus icon (+), then click on `select a port to view on host1` and enter the port `3333`

