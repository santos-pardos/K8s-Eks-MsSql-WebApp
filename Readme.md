## Links
https://rajanieshkaushikk.com/2021/02/27/how-to-deploy-sql-server-containers-to-a-kubernetes-cluster-for-high-availability/


## EKS Secret
kubectl create secret generic mssql-secret --from-literal=SA_PASSWORD="example_123"


## Secrets
echo -n "example_123" | base64                                                                                                                           
ZXhhbXBsZV8xMjM=

## CI/CD ArgoCD
```
eksctl get cluster
aws eks update-kubeconfig --name demo-cluster --region us-east-1

kubectl create namespace argocd 
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
export ARGOCD_SERVER=`kubectl get svc argocd-server -n argocd -o json | jq --raw-output '.status.loadBalancer.ingress[0].hostname'`
echo $ARGOCD_SERVER
export ARGO_PWD=`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d`
echo $ARGO_PWD
(user argocd=admin)

Repositories : git - default  - https://github.com/santos-pardos/K8s-Eks-MsSql-WebApp.git and Connect
New App; tetris - default - Automatic - https://github.com/santos-pardos/K8s-Eks-MsSql-WebApp.git - manifests  - https://Kubernetes.default.svc - default - Create

kubectl get all
kubectl delete svc argocd-server -n argocd
```
