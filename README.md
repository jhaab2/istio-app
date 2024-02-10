ISTIO 
To install it on minikube, it needs more resources, so set it - 
./minikube start --cpus 6 --memory 3900 
Download istio from [here](https://istio.io/latest/docs/setup/getting-started/#ip).
How to install ?
istioctl install --set profile=demo -y 

bash-3.2$ kubectl get ns [ Check a namespace created for istio ]
istio-system           Active   29m

We label a namespace with istio-injection enabled, then only new pods in that name space will be created with istio envoy-proxy

kubectl get ns default --show-labels [ This show-labels attribute can be used with other objects as well, such as pods. ]

kubectl label namespace default istio-injection=enabled

Now, deploy all the yaml files. 

login to client pod -

kubectl exec -it client -- /bin/sh

while true; do curl hello-app-service:8080; sleep .1; done
