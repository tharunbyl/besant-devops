## kubernets cluster(container orchestrator)

pod, node, worker

            KUBERNETE CLUSTER

                master
        /          |        \
worker1          worker2         worker3
o o o            o o o           o o o
o o o            o o o           o o o
Docker           Docker          Docker


NOTE: 
1. if worker is down, another is created by master
2. if master is down, until the next request comes cluster is continued to run. Hence need to create multiple master, keeping one of them as leader/primary 


+---------------------------+
|           Monolith        |
+---------------------------+
| +----------+ +----------+ |
| | App 1    | | App 2    | |
| +----------+ +----------+ |
| +----------+ +----------+ |
| | App 3    | | App 4    | |
| +----------+ +----------+ |
+---------------------------+

## Kuberetes providers:

                        KUBERNETS
    /          |             |           |         \          
EKS            AKS          GKE          RKE     Openshift
AWS            Azure        

## Architecture of Kubernetes:

![alt text](image.png)

Control flow
a. K8s Admin(UI/CLI)
        \/
Control panel
a. API Server
b. Scheduler

Workder Node
a. create pods, instructed by API Server

Control Panel
a. etcd DB
b. Control Manager




1. K8s Admin (UI / CLI)
+ deploy app with 3 container

2. Control Panel
+ Kube API Server
+ Kube Scheduler
+ etcd Database
+ control manager
    - node controller - node
    - replication controller - pod
    - endpoint controller - manage/association with service and pod

3. Worker Node
+ Kublet - create pods
+ KubeProxy - entry for the traffic between pods

![alt text](image-1.png)


## Installation 

ec2 -> 3 server -> name -> ubuntu 22.0 -> key value -> all traffic -> cpu t3 medium -> storage gp3 25

Kubernets-Master
Kubernets-Worker1
Kubernets-Worker2

login into 3 as sudo su -

update private ips

vi /etc/hosts // local dns


namespace - multiple physical and single virtual 

namespace   namespace    namespace
A            B              C

App1         2              3

dev          qa             pre-prod


vi pod1.yaml
kubectl apply -f pod1.yaml
kubectl get pods
kubectl get pods -o wide
kubectl exec -it first-prod -- bash
apt update -y
exit
kubectl describe pod first-pod
kubectl logs first-pod
kubectl delete pod first-pod
kubectl get rs
kubectl delete deployment <name>

### Replica Set
replicas: n // n=3, etc

Drawback: image updates


### Deployments

Strategies 
#### recreate  Deployment

#### rolling update Deployment
maxSurge
maxUnavailable   
#### Canary Deployment
5 -> 50 -> 100
#### Blue/green Deployment
blue - current infra
green - new infra