# eks_cluster

## Pre-requisities
1. Install kubectl on your machine
- mac: `brew install kubectl`
- windows (run Powershell as Adminstrator): `choco install kubernetes-cli`
- run `kubectl version --client` to verify installation

2. Install eksctl on your machine
- mac: `brew install eksctl`
- windows (run Powershell as Adminstrator): `choco install eksctl`
- run `eksctl version` to verify installation

3. Create a new Github Repo and clone it locally
- ceate a file 'cluster.yaml', this file is used to create your EKS cluster aw well as your worker nodes
- run
```sh
eksctl create cluster -f cluster.yaml
```
will create you infrastructure, this will create a Cloudformation template and deploy it in your account

4. To view config file created
- mac directory: ~.kube/config
- windows: C:/Users/<your user>/config
run following to verify cluster creation
```sh
kubectl get node
kubectl get node -o wide
```

5. Commands
can refer to kubectl commands cheat sheet
```sh
kubectl get pod -A
kubectl describe nodes
kubectl describe nodes <name of node>
```
6. Deploying a sample hello world application
- create a file called `k8s-deployment.yaml`
- to deploy: run `kubectl apply -f k8s-deployment.yaml`

7. Exposing your hello world app through a load balancer
- create a file called `service.yaml`
- to deploy: run `kubectl apply -f service.yaml`
- view you service: `kubectl get svc`
This will show external DNS name, which is also the load balancer DNS. Copy the DNS and paste into your browser to view your application live.

8. Cleanup
```sh
kubectl get deployment
kubectl delete deployment <name of deployment>
eksctl delete cluster --name <name of your cluster>