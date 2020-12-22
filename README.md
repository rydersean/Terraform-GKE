# Terraform-GKE-Kubernetes-SignalFx

Launch and manage a GKE cluster using Terraform.

## Clone Terraform-GKE-Kubernetes-SignalFx

git clone https://github.com/rydersean/Terraform-GKE-Kubernetes-SignalFx.git

mkdir secrets directory

download My_project_XXX-XXXXXXX.json from GCP to secrets/

echo "YOUR_ACCESS_TOKEN" > secrets/token

Edit the variables.tf file
* change the project to your project_id found in your My_Project_XXX-XXXXXX.json file.
* Change name to something like yourname-demo-k8s-cluster

## Launch GKE Cluster

```
$ terraform init
$ terraform apply
```

If you see this error:
Error: Error waiting for creating GKE cluster: 
	(1) insufficient quota to satisfy the request: Not all instances running in IGM after 14.031293531s. Expected 1, running 0, transitioning 1. Current errors: [GCE_QUOTA_EXCEEDED]: Instance 'gke-sfx-cluster-default-pool-e6dc32dc-3xh4' creation failed: Quota 'INSTANCES' exceeded.  Limit: 8.0 in region us-central1

Change to another location where you do have quota such as "us-east4-c"

Change the location in your variables.tf

## Launch Demo Application

First, you will need to authenticate to the cluster, then you can run the following:

```
$ kubectl apply -f deployment.yaml
$ kubectl apply -f service.yaml
$ kubectl apply -f ingress.yaml
```

*Note: It will take 5 minutes for the load balancer to provision*

## Deploying SignalFx

To install the SFx smartagent using helm - https://docs.signalfx.com/en/latest/integrations/kubernetes/k8s-quick-install.html
