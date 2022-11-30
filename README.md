# argocd1

Bajarse el repo actual

git clone https://github.com/diegochavezcarro/argocd1.git

Entrar en el directorio argocd1

1. Instalar ArgoCD (https://argo-cd.readthedocs.io/en/stable/getting_started/):

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

2. Hacer port forwarding para poder acceder al dashboard de ArgoCD:

kubectl port-forward svc/argocd-server -n argocd 8080:443

Se podra acceder por browser a localhost:8080, aceptar el certificado no valido.

3. Obtener la password de ArgoCD:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

Copiarla y hacer login con username admin y esa password.

4. Desplegar el Application:

Primero bajarselo:

wget https://raw.githubusercontent.com/diegochavezcarro/argocd1/main/guestbook-app.yaml

Instalarlo:

kubectl apply -f guestbook.yaml

Observar el dashboard de ArgoCD.

5. Sincronizar en el dashboard. Observar como se despliega todo.

6. Borrar en el dashboard el deployment. Sincronizar. Lo mismo por terminal y de vuelta Sincronizar
el dashboard.

7. Agregar una replica mas en el deployment. Sincronizar y observar como se actualiza.


