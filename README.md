# canary

https://istio.io/latest/docs/setup/getting-started/#download


canary:
https://dev.to/stack-labs/canary-deployment-with-argo-cd-and-istio-406d


bluegreen
https://blog.baeke.info/2021/11/01/kubernetes-blue-green-deployments-with-argo-rollouts/


kubectl debug -it colorapi-f7cb564b6-z29xn  -n default --image=jfrog.fkinternal.com/transact-commons/debug-image:latest  --target=colorapi


canary
https://particule.io/en/blog/argocd-canary/
portforward the svc
appname=http://localhost:63631/

while true; do curl -s $appname | jq .color; sleep 0.5; done




argocd
https://argo-cd.readthedocs.io/en/stable/getting_started/

step 2:
https://tanzu.vmware.com/developer/guides/argocd-gs/

argocd app create colorapi --repo https://github.com/kabilanmani93/canary.git --path . --dest-server https://kubernetes.default.svc --dest-namespace default

https://argoproj.github.io/argo-rollouts/features/traffic-management/istio/
