# Terraform-GKE

Launch and manage a GKE cluster using Terraform.

## Launch GKE Cluster

```
$ terraform init
$ terraform plan
$ terraform apply
```

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
