# Kudo installation and deploy test java application
I assume that minikube/EKS/K8S cluster already installed  
  ## 1. Installation cert-manager  
```
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.1/cert-manager.yaml
kubectl get pods --namespace cert-manager # to check if pods are running
```
  ## 2. Init kudo  
```
kubectl kudo init --version 0.17.0
```
  ## 3. Build test docker container  
  You need to clone hello-world repo first!  
```
git clone https://github.com/helli0n/hello-java-docker.git
```  
   Use README for build docker image, that we will use later for deployments
  ## 4. Deploy app using kudo  
  You need to clone git repo with kudo operator for deployment it  
```
git clone https://github.com/helli0n/k8s-operator-kudo.git
cd k8s-operator-kudo
kubectl kudo install operator/
```
When you see that application has started, you should run kubectl port-forward command to get access to the service
```
kubectl port-forward service/hello-app 8080
```
Application is accessible by URL http://127.0.0.1:8080/  
If you get access to the application it means that you successfully installed your first k8s operator.
