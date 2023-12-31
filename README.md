# FastApi-Kubernetes-Tekton
Base project from git@github.com:atlekbai/fastapi-boilerplate.git  
## Description
Task:

1. Install Tekton in Kubernetes cluster.

2. Using Tekton please create pipeline to build and deploy Python FastApi application.

Results: building pipeline, running application in cluster.  

## Implementation
Cluster created on GCP.    
Filestore CSI driver - Enable  
Install kubectl  
Tekton:  
Replace LINK-TO-THE-PACKAGE with the package URL you would like to use.
https://github.com/tektoncd/cli/releases  
curl -LO LINK-TO-THE-PACKAGE  
sudo dpkg -i ./PACKAGE-NAME  

gcloud services enable container.googleapis.com

gcloud container clusters create tekton-cluster \
  --num-nodes=<nodes> \
  --region=<location> \
  --workload-pool=<project-id>.svc.id.goog
kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml  
## Build
  
kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

tkn hub install task git-clone  
tkn hub install task kaniko  

kubectl apply -f docker-credentials.yaml     
kubectl apply -f secrets_git.yaml  
kubectl apply -f pipe_clone.yaml   
kubectl create -f pipe_run_clone.yaml    

tkn pipelinerun logs  clone-build-push-run-**** -f

## Deploy
kubectl apply -f https://api.hub.tekton.dev/v1/resource/tekton/task/helm-upgrade-from-source/0.1/raw  
kubectl apply -f volume.yaml  
kubectl apply -f pvc.yaml  
kubectl -n default create serviceaccount helm-pipeline-run-sa  
kubectl -n default create rolebinding helm-pipeline-run-sa-edit --clusterrole edit --serviceaccount default:helm-pipeline-run-sa -o yaml --dry-run=client | kubectl apply -f -  
kubectl apply -f pipe.yaml  
kubectl apply -f pipe_run.yaml  

  
  




