# FastApi-Kubernetes-Tekton
Base project from git@github.com:atlekbai/fastapi-boilerplate.git  
## Description
Task:

1. Install Tekton in Kubernetes cluster.

2. Using Tekton please create pipeline to build and deploy Python FastApi application.

Results: building pipeline, running application in cluster.  

##Implementation

kubectl
helm

Tekton
# Replace LINK-TO-THE-PACKAGE with the package URL you would like to use.
https://github.com/tektoncd/cli/releases
curl -LO LINK-TO-THE-PACKAGE
sudo dpkg -i ./PACKAGE-NAME




gcloud services enable container.googleapis.com

gcloud container clusters create tekton-cluster \
  --num-nodes=<nodes> \
  --region=<location> \
  --workload-pool=<project-id>.svc.id.goog
  
kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
  
  
  




