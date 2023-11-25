# minikube-argocd-tekton

## argocd

step 1:
```
kubectl create ns argocd
```

step 2:
```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.8/manifests/install.yaml
```

step 3:
```
kubectl get all -n argocd
```

step 4:
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

step 5:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

## tekton

step 6:
```
kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```

step 7:
```
kubectl get pods --namespace tekton-pipelines --watch
```

step 8:
```
kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/dashboard/latest/release-full.yaml
```

step 9:
```
kubectl get pods --namespace tekton-pipelines --watch
```

step 10:
```
kubectl port-forward -n tekton-pipelines service/tekton-dashboard 9097:9097
```
