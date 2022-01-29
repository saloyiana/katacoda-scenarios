## To demonstrate the gitops concept: 
Open the source (your git repo), change the version to 2 (`e.g., gcr.io/heptio-images/ks-guestbook-demo:0.2`), 

Now check the status of argocd application, it should be `outofsync` which means there is a difference between your source and destination, 
Click on `app diff` to check out the differences, click on `sync` to deploy the new version and check out the app again.

## Challenge: 
Create the same argocd application but in a declarative way.
### Hint: 
After writting the yaml file, use `kubectl apply -f <filename> -n argocd` command to create it. 
then checkout the Argocd UI. 


Don't forget to share the result with us.  
  
