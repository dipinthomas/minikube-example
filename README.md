# Minikube Deployment

Minikube quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. Minikube focus on helping application developers and new Kubernetes users.

# Assumptions

1. Minikube is [installed](https://minikube.sigs.k8s.io/docs/start/) 
2. kubectl is [installed](https://kubernetes.io/docs/tasks/tools/)
3. Minikube should be initiated with extended port range, instead of default 30000-32000

>  minikube start --extra-config=apiserver.service-node-port-range=1-65535

# Validate Installtion 

kubectl is used to interact with kubernetes API. kubeconfig is located in the users home directory (~/.kube/config).

Login with the user which has access to kube API and execute below command.

> Kubectl get node

Expected result is  master node details

# Deployment 

Clone this repository & update image name in the yaml if required or changed. 

>  kubectl -f minikube-example

# Access Web UI

Minikube provides a handy command to find service url:

> minikube service frontend --url

Response : `http://192.168.49.2:80`


> minikube service proxy --url

Response: `http://192.168.49.2:5000`

# Deployment Verification

## Find backend/proxy url

> minikube service proxy --url

> curl http://192.168.49.2:5000/stats

 *{"cpu":23.1,"ram":28.8}*

