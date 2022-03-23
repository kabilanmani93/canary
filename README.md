# canary

https://istio.io/latest/docs/setup/getting-started/#download


canary:
https://dev.to/stack-labs/canary-deployment-with-argo-cd-and-istio-406d


bluegreen
https://blog.baeke.info/2021/11/01/kubernetes-blue-green-deployments-with-argo-rollouts/


kubectl debug -it colorapi-f7cb564b6-z29xn  -n default --image=jfrog.fkinternal.com/transact-commons/debug-image:latest  --target=colorapi


canary
https://particule.io/en/blog/argocd-canary/
portforward the svc : kubectl port-forward svc/argocd-server -n argocd 8080:443
appname=http://127.0.0.1:8001/api/v1/namespaces/default/services/colorapi:http/proxy/


curl -s http://127.0.0.1:8001/api/v1/namespaces/default/services/colorapi:http/proxy/ | jq .color
while true; do curl -s $appname | jq .color; sleep 0.5; done




argocd
https://argo-cd.readthedocs.io/en/stable/getting_started/

argo-rollouts
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://raw.githubusercontent.com/argoproj/argo-rollouts/stable/manifests/install.yaml

step 2:
https://tanzu.vmware.com/developer/guides/argocd-gs/

argocd app create colorapi --repo https://github.com/kabilanmani93/canary.git --path . --dest-server https://kubernetes.default.svc --dest-namespace default
argocd app sync colorapi

Minikube:
minikube start  --extra-config=apiserver.enable-swagger-ui=true
https://medium.com/@Oskarr3/setting-up-ingress-on-minikube-6ae825e98f82

k8 api:
http://127.0.0.1:8001/api/v1/namespaces/default/services/colorapi:http/proxy/

Rollout:
https://argoproj.github.io/argo-rollouts/features/canary/