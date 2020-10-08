# Kubernetes Playground

My playground project to get some practice with kubernetes.

It includes instructions for how to setup a local cluster and a example application. 

## Setup Cluster & Tools

### minikube

Install local kubernetes cluster:

https://kubernetes.io/de/docs/tasks/tools/install-minikube/#linux

#### Ingress Addon
    
In order to use your service from outside of the cluster you need a implementation of a ingress controller installed.

    # install k8s nginx implementation of Ingress
    $ minikube addons enable ingress
    
    # verify if ngnix controller is running
    $ kubectl get pod -n kube-system

#### Commands
    
    # starts the cluster
    $ minikube start
    
    # stops the cluster
    $ minikube stop
    
    # deletes the cluster
    $ minikube delete
 
### CLIs

* [kubectl](https://github.com/kubernetes/kubectl): Main Commandline Tool for kubernetes
* [krew](https://github.com/kubernetes-sigs/krew): Tool for installing plugins
* [kubectx & kubens](https://github.com/ahmetb/kubectx): kubectx let you switch contexts, kubens let you switch namespaces


## Setup Application
         
    # 1. create namespace, app, ingress
    $ kubectl apply -f namespace.yaml -f app.yaml -f ingress.yaml

    # 2. wait for external ip (can take a minute)
    $ kubectl get ingress -n chrgue --watch
    
    # 3. configure /etc/hosts
    $ sudo vim /etc/hosts 
    
    # 4. Test
    $ curl http://k8s.chrgue.com/
    
## Resources

* [YouTube - Complete Kubernetes Tutorial for Beginners](https://www.youtube.com/watch?v=VnvRFRk_51k&list=PLy7NrYWoggjziYQIDorlXjTvvwweTYoNC)





 
  

