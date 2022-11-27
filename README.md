# argocd1
https://argo-cd.readthedocs.io/en/stable/getting_started/

1. Instalar ArgoCD:
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

2. Hacer port forwarding para poder acceder al dashboard de ArgoCD:
kubectl port-forward svc/argocd-server -n argocd 8080:443
Se podra acceder por browser a localhost:8080, aceptar el certificado no valido.

3. Obtener la password de ArgoCD:
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
Copiarla y hacer login con username admin y esa password.

4. Desplegar el 
