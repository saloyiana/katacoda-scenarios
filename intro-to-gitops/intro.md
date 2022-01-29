## What is GitOps?
GitOps is a way to do Kubernetes cluster management and application delivery. It works by using Git as a single source of truth for declarative infrastructure and applications. With GitOps, the use of software agents can alert on any divergence between Git with what's running in a cluster, and if there's a difference, Kubernetes reconcilers automatically update or rollback the cluster depending on the case. With Git at the center of your delivery pipelines, developers use familiar tools to make pull requests to accelerate and simplify both application deployments and operations tasks to Kubernetes.

## ArgoCD
Application definitions, configurations, and environments should be declarative and version controlled. Application deployment and lifecycle management should be automated, auditable, and easy to understand. Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes that utilizes these principles.

## Lab Content 
1. Argocd Installation.
2. Argocd Source Configuration.
3. Argocd Application Creation.
4. Challenge. 
